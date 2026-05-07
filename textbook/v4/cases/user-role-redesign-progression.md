# User and Role Redesign Progression

## Purpose

This note records the intended teaching progression for redesigning the person-related parts of the tutoring and clinic cases.

Use the simple initial cases early. Bring up the redesign later, after students have enough database-design experience to evaluate why the redesign is better and what it costs.

## Instructional Timing

### Modules 1-6

Use the initial designs.

Reason:

- the tables are easier to read
- the ERDs are easier to draw
- the DBDDs are easier to implement
- beginner SQL is easier to write
- students can learn the core workflow without premature abstraction

### Module 7

Introduce pressure for redesign through permissions and role-based access.

Prompt students to notice that people in a system often need accounts and permissions, not just business-object records.

### Module 8

Introduce the redesign request.

Students should compare the initial design with a more flexible `User` and `Role` model and explain what changes across the ERD, DBDD, SQL, views, procedures, triggers, permissions, and tests.

## Tutoring Center Initial Design

The primary case begins with separate person-related tables:

```text
Student
Tutor
Staff
```

This design is acceptable early in the course because students can see the roles clearly.

## Tutoring Center Redesign Goal

Later, Lakeside may decide that every person who logs into the system should have one user identity. A person may hold more than one role over time.

Redesigned person model:

```text
User(
    UserID PK,
    FirstName,
    LastName,
    EmailAddress,
    PhoneNumber,
    Active
)

Role(
    RoleID PK,
    RoleName
)

UserRole(
    UserID PK/FK,
    RoleID PK/FK,
    AssignedDate,
    EndDate
)

StudentProfile(
    UserID PK/FK,
    GradeLevel,
    SchoolName
)

TutorProfile(
    UserID PK/FK,
    HireDate,
    HourlyRate
)

StaffProfile(
    UserID PK/FK,
    StaffRole,
    HireDate
)
```

The tutoring case does not need a forced recursive relationship. Its redesign value comes from shared identity, role flexibility, and permissions.

## Clinic Initial Design

The alternative clinic case begins with separate person-related tables:

```text
Patient
Guardian
Provider
```

This design is acceptable early because each role is concrete and easy to model.

## Clinic Redesign Goal

Later, the clinic may decide that all people in the system should be modeled as users with roles. This matters because the same person may appear in more than one role, and because relationships between people are central to the case.

Redesigned person model:

```text
User(
    UserID PK,
    FirstName,
    LastName,
    EmailAddress,
    PhoneNumber,
    Active
)

Role(
    RoleID PK,
    RoleName
)

UserRole(
    UserID PK/FK,
    RoleID PK/FK,
    AssignedDate,
    EndDate
)

PatientProfile(
    UserID PK/FK,
    DateOfBirth
)

GuardianProfile(
    UserID PK/FK,
    PreferredContactMethod
)

ProviderProfile(
    UserID PK/FK,
    Credential,
    LicenseNumber
)
```

## Clinic Recursive Relationships

The clinic redesign can naturally include recursive relationships because patients, guardians, and providers are all users.

```text
PatientGuardian(
    PatientUserID PK/FK REFERENCES User(UserID),
    GuardianUserID PK/FK REFERENCES User(UserID),
    RelationshipType,
    IsPrimaryContact
)

ProviderSupervisor(
    ProviderUserID PK/FK REFERENCES User(UserID),
    SupervisorUserID PK/FK REFERENCES User(UserID),
    StartDate,
    EndDate
)
```

These are recursive relationships on `User`. Use these labels consistently:

- `PatientGuardian` is a recursive network / self-referencing `M:N` / `N:M`
  pattern: one user may be a guardian for many patient users, and one patient
  user may have many guardian users.
- `ProviderSupervisor` is a recursive hierarchy / self-referencing `1:N`
  pattern when the rule says one provider may supervise many provider users and
  one provider user may have zero or one current supervising provider.

## Why The Redesign Is Better

The redesign is better when the organization needs identity, access, and role flexibility.

Benefits:

- one person has one identity across the system
- contact information is stored once
- a person can hold multiple roles
- permissions can be tied to roles more cleanly
- role changes over time can be recorded
- cross-role reporting becomes easier
- clinic person-to-person relationships become explicit and teachable

## Problems If The Design Is Not Revised

If the original separate-table design is kept after the organization needs one account model, these problems can appear:

- the same person may be duplicated across multiple tables
- names, emails, and phone numbers may become inconsistent
- permissions may be copied or hard-coded by table instead of managed by role
- a person with multiple roles may require awkward duplicate records
- reporting across all people becomes harder
- later requirements may require fragile patches instead of a coherent design change
- AI-generated schema changes may solve one local issue while leaving the larger model inconsistent

## Why Not Use The Redesign First?

The redesign is more flexible, but it is also more abstract. If introduced too early, students may focus on the abstraction instead of learning the basic workflow.

The initial design is better for early learning.

The redesigned model is better for late-course judgment, comparison, and revision.

## Module 8 Change Request Prompt

Use this prompt or a variant:

```text
The organization has grown. People now need one login identity across roles, and some people may hold more than one role over time. Redesign the person-related part of the database using User, Role, and role-specific profile tables. Explain what changes in the ERD, DBDD, SQL implementation, permissions, views, procedures, triggers, and tests.
```

For the clinic alternative case, add:

```text
Guardians and patients are both users, and providers may supervise other providers. Represent these person-to-person relationships in the redesigned model.
```
