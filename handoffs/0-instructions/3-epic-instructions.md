# Epic Management System

## Purpose
Epics consolidate related milestones when:
- Multiple related features form a complete domain
- System capabilities span several milestones
- Core architectural patterns emerge
- Product capabilities reach maturity

## Core Principles
- **Architectural**: Focus on system design and capabilities
- **Cohesive**: Group functionally related milestones
- **Reusable**: Capture patterns across implementations
- **Domain-Focused**: Organize by business domain or technical area
- **Knowledge Transfer**: Optimize for future team members

## Milestone to Epic
1. **Accumulate Milestones First**:
   - Complete feature implementations as milestones
   - Let 2-4 related milestones accumulate
   - Group milestones by functional domain or system area
   - Identify architectural patterns across milestones

2. **Consolidate to Epics**:
   - Create E-prefixed epic directories (E1-authentication, E2-data-layer)
   - Move related milestone directories into the epic
   - Preserve all milestone and handoff content
   - Create architectural and pattern summaries

## Workflow
1. **Development Progression**:
   - Handoffs → capture daily work
   - Milestones → summarize completed features
   - Epics → consolidate system capabilities

2. **Epic Creation**:
   - Create epic directory with E-prefix numbering
   - Use descriptive domain-oriented names
   - Move relevant milestone folders intact
   - Create summary documents focused on architecture
   - Preserve all milestone and handoff content

## Epic Documents
1. **0-epic-summary.md**:
   - System capabilities implemented
   - Architectural decisions
   - Domain model evolution
   - Integration points
   - Cross-cutting concerns

2. **0-epic-lessons.md**:
   - Cross-milestone patterns
   - Architectural insights
   - Performance considerations
   - Scalability strategies
   - Infrastructure lessons

## Naming Convention
- Epic directories: E-prefixed numbers (E1-authentication-system)
- Epic summaries: 0-prefixed names (0-epic-summary.md)
- Milestone directories: maintain original numbering within epics

## Writing Style

### 0-epic-summary.md
```
## System Capabilities
- Complete authentication flow with SSO integration
- Role-based access control with dynamic permissions
- Audit logging with compliance reporting

## Architectural Decisions
- Stateless JWT authentication with 15-min refresh
- Microservice boundary at identity domain
- Shared permission model between services

## Domain Model
- Identity entities: User, Role, Permission
- Relationship model: many-to-many via junction
- Shared constants for system-wide roles

## Integration Points
- Login providers: Google, GitHub, Email
- Service boundaries: via event bus
- Client integration: via identity SDK
```

### 0-epic-lessons.md
```
## Authentication Patterns

**Challenge**: Service-to-service authentication with proper scope limits

**Solution**:
- Fixed service identities with capability tokens
- Scope inheritance model with mandatory revalidation
- Circuit-breaker pattern for auth service outages

## Performance Optimization

**Challenge**: Authorization checks causing API latency

**Solution**:
- Permission caching with 5-minute TTL
- Parallel permission validation
- Cache invalidation via event subscription
```

## Example Organization
Before:
```
handoffs/
├── 1-user-auth/
│   ├── 0-milestone-summary.md
│   ├── 0-lessons-learned.md
│   ├── 1-login-setup.md
│   └── 2-auth-flow.md
├── 2-permission-system/
│   ├── 0-milestone-summary.md
│   ├── 0-lessons-learned.md
│   ├── 3-role-definition.md
│   └── 4-permission-checks.md
├── 3-audit-logging/
│   ├── 0-milestone-summary.md
│   ├── 0-lessons-learned.md
│   ├── 5-event-capture.md
│   └── 6-compliance-reports.md
```

After:
```
handoffs/
├── E1-identity-management/
│   ├── 0-epic-summary.md
│   ├── 0-epic-lessons.md
│   ├── 1-user-auth/
│   │   ├── 0-milestone-summary.md
│   │   └── ...
│   ├── 2-permission-system/
│   │   ├── 0-milestone-summary.md
│   │   └── ...
│   └── 3-audit-logging/
│       ├── 0-milestone-summary.md
│       └── ...