# Epic Reorganization Functions

These one-liner functions create a new epic folder within handoffs/ and move selected milestone directories into it.

## Bash
```bash
# Generate next epic number by finding the highest existing E-prefixed directory
epic_num=$(find handoffs/ -maxdepth 1 -type d -name "E[0-9]*-*" 2>/dev/null | wc -l | xargs test "0" -eq && echo "1" || find handoffs/ -maxdepth 1 -type d -name "E[0-9]*-*" | sort -V | tail -n1 | sed -E 's/.*\/E([0-9]+).*/\1/' | awk '{print $1+1}'); 

# Create epic directory
mkdir -p "handoffs/E${epic_num}-epic-name"; 

# Replace these numbers with the actual milestone numbers you want to include
milestones_to_move="2 3 5"; 

# Move specified milestone directories into the epic directory
for num in $milestones_to_move; do
  find handoffs/ -maxdepth 1 -type d -name "${num}-*" -exec mv {} "handoffs/E${epic_num}-epic-name/" \;
done
```

## PowerShell
```powershell
# Generate next epic number by finding the highest existing E-prefixed directory
$epic_num = if (!(Get-ChildItem "handoffs" -Directory | Where {$_.Name -match "^E\d+-"})) {1} else {(Get-ChildItem "handoffs" -Directory | Where {$_.Name -match "^E\d+-"} | ForEach {[int]($_.Name -match "E(\d+)-" | ForEach {$Matches[1]})} | Measure -Max).Maximum + 1}; 

# Create epic directory
New-Item -Path "handoffs/E${epic_num}-epic-name" -ItemType Directory -Force; 

# Replace these numbers with the actual milestone numbers you want to include
$milestones_to_move = @("2", "3", "5"); 

# Move specified milestone directories into the epic directory
foreach ($num in $milestones_to_move) {
  Get-ChildItem -Path "handoffs" -Directory -Filter "${num}-*" | Move-Item -Destination "handoffs/E${epic_num}-epic-name/"
}
```

## Python
```python
import os, re, shutil

# Generate next epic number by finding the highest existing E-prefixed directory
epic_dirs = [d for d in os.listdir("handoffs") if os.path.isdir(os.path.join("handoffs", d)) and re.match(r"E\d+-", d)]
epic_num = 1 if not epic_dirs else max([int(re.match(r"E(\d+)-", d).group(1)) for d in epic_dirs]) + 1

# Create epic directory
epic_dir = f"handoffs/E{epic_num}-epic-name"
os.makedirs(epic_dir, exist_ok=True)

# Replace these numbers with the actual milestone numbers you want to include
milestones_to_move = ["2", "3", "5"]

# Move specified milestone directories into the epic directory
for num in milestones_to_move:
    for d in os.listdir("handoffs"):
        dir_path = os.path.join("handoffs", d)
        if os.path.isdir(dir_path) and d.startswith(f"{num}-"):
            shutil.move(dir_path, os.path.join(epic_dir, d))
```

## Node.js
```javascript
const fs = require('fs'), path = require('path');

// Generate next epic number by finding the highest existing E-prefixed directory
const epic_dirs = fs.readdirSync('handoffs').filter(d => 
    fs.statSync(path.join('handoffs', d)).isDirectory() && /^E\d+-/.test(d));
const epic_num = epic_dirs.length === 0 ? 1 : 
    Math.max(...epic_dirs.map(d => parseInt(d.match(/^E(\d+)-/)[1]) || 0)) + 1;

// Create epic directory
const epic_dir = path.join('handoffs', `E${epic_num}-epic-name`);
fs.mkdirSync(epic_dir, { recursive: true });

// Replace these numbers with the actual milestone numbers you want to include
const milestones_to_move = ["2", "3", "5"];

// Move specified milestone directories into the epic directory
milestones_to_move.forEach(num => {
    fs.readdirSync('handoffs')
        .filter(d => fs.statSync(path.join('handoffs', d)).isDirectory() && 
                d.startsWith(`${num}-`))
        .forEach(d => fs.renameSync(
            path.join('handoffs', d), 
            path.join(epic_dir, d)
        ));
});
```

## Important Usage Notes

1. Replace "epic-name" with a descriptive name for your epic (e.g., "authentication-system")
2. Replace the milestone numbers in `milestones_to_move` with the actual milestone numbers you want to include in this epic
3. These scripts only move the milestone directories; you still need to create the 0-epic-summary.md and 0-epic-lessons.md files
4. Always verify the script has correctly identified your milestones before executing

For example, if you want to create an epic for your API system that includes milestones 2, 4, and 7:

1. Change "epic-name" to "api-system"
2. Set milestones_to_move to "2 4 7" (Bash), @("2", "4", "7") (PowerShell), or ["2", "4", "7"] (Python/Node.js)
3. Execute the script
4. Create the summary documents within the new epic directory