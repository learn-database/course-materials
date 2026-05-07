# Cedar Valley Community Clinic Alternative Case

## Role In The Course

Cedar Valley Community Clinic is the alternative case for further discussion, comparison, and extension activities.

Use this case when a lesson needs a richer example involving:

- privacy and appropriate access
- multiple person roles
- insurance and claims
- scheduling and clinical service records
- recursive relationships in a later redesign

Do not make this the default case for every lesson. The tutoring center remains the primary running case.

## Initial Case Narrative

Cedar Valley Community Clinic provides basic wellness appointments. Staff members track patients, guardians, providers, appointments, rooms, services, appointment notes, invoices, payments, insurance policies, and insurance claims.

Patients may have guardians. Providers perform appointments and may have specialties. Each appointment is scheduled in one room and may include one or more services. Some appointments generate invoices. Some invoices are paid directly by patients or guardians, and some are submitted to insurance.

## Initial Design Goal

The initial design is still approachable, but it is richer than the tutoring case. It gives instructors an alternative case for discussion or advanced practice without replacing the tutoring center as the primary example.

## Initial Table Set

Use this as the simple early-course clinic model:

- `Patient`
- `Guardian`
- `PatientGuardian`
- `Provider`
- `Specialty`
- `ProviderSpecialty`
- `Room`
- `Appointment`
- `Service`
- `AppointmentService`
- `AppointmentNote`
- `Invoice`
- `Payment`
- `InsurancePolicy`
- `InsuranceClaim`

## Relationship Patterns

| Pattern | Relationship |
|---|---|
| `M:N` | `Patient` and `Guardian` through `PatientGuardian` |
| `M:N` | `Provider` and `Specialty` through `ProviderSpecialty` |
| `1:N` | one `Patient` may have many `Appointment` records |
| `1:N` | one `Provider` may handle many `Appointment` records |
| `1:N` | one `Room` may be used for many `Appointment` records |
| `M:N with attributes` | `Appointment` and `Service` through `AppointmentService` |
| optional dependent record | one `Appointment` may have zero or more `AppointmentNote` records |
| optional `1:1` | one `Appointment` may produce zero or one `Invoice` |
| `1:N` | one `Invoice` may have many `Payment` records |
| optional `1:N` | one `Patient` may have zero or many `InsurancePolicy` records |
| optional `1:N` | one `InsurancePolicy` may have zero or many `InsuranceClaim` records |
| recursive hierarchy / self-referencing `1:N` | later redesign: one `Provider` may supervise many other `Provider` users |
| recursive network / self-referencing `M:N` / `N:M` | later redesign: patient, guardian, and provider user-to-user relationships through a relationship table |

## DBDD-Ready Table List

```text
Patient(
    PatientID PK,
    FirstName,
    LastName,
    DateOfBirth,
    EmailAddress,
    PhoneNumber,
    Active
)

Guardian(
    GuardianID PK,
    FirstName,
    LastName,
    EmailAddress,
    PhoneNumber
)

PatientGuardian(
    PatientID PK/FK,
    GuardianID PK/FK,
    RelationshipType,
    IsPrimaryContact
)

Provider(
    ProviderID PK,
    FirstName,
    LastName,
    Credential,
    EmailAddress,
    Active
)

Specialty(
    SpecialtyCode PK,
    SpecialtyName
)

ProviderSpecialty(
    ProviderID PK/FK,
    SpecialtyCode PK/FK
)

Room(
    RoomID PK,
    RoomName,
    Capacity
)

Appointment(
    AppointmentID PK,
    PatientID FK,
    ProviderID FK,
    RoomID FK,
    AppointmentDate,
    StartTime,
    Status
)

Service(
    ServiceCode PK,
    ServiceName,
    StandardCharge
)

AppointmentService(
    AppointmentID PK/FK,
    ServiceCode PK/FK,
    Quantity,
    ChargeAmount
)

AppointmentNote(
    AppointmentNoteID PK,
    AppointmentID FK,
    NoteText,
    CreatedAt
)

Invoice(
    InvoiceID PK,
    AppointmentID FK UNIQUE,
    InvoiceDate,
    TotalAmount,
    Status
)

Payment(
    PaymentID PK,
    InvoiceID FK,
    PaymentDate,
    PaymentAmount,
    PaymentMethod
)

InsurancePolicy(
    PolicyID PK,
    PatientID FK,
    CarrierName,
    PolicyNumber,
    Active
)

InsuranceClaim(
    ClaimID PK,
    PolicyID FK,
    InvoiceID FK,
    ClaimDate,
    ClaimStatus,
    ClaimAmount
)
```

## What This Case Teaches Well

- Privacy and role-based access judgment.
- Multiple person-role tables in the initial design.
- More advanced many-to-many relationships.
- Optional billing and insurance relationships.
- Natural late-course redesign into `User`, `Role`, and recursive user-to-user relationships.
- Recursive hierarchy as a self-referencing `1:N` pattern.
- Recursive network as a self-referencing `M:N` / `N:M` pattern.

## Later Redesign Opportunity

This case is the stronger place to introduce recursive relationships. In the later redesign, `Patient`, `Guardian`, and `Provider` can become role-specific profiles attached to a shared `User` table.

That redesign makes relationships such as guardian-to-patient and provider-to-provider supervision explicit user-to-user relationships. Use these labels consistently:

- `recursive hierarchy`: a self-referencing `1:N` pattern, such as one provider supervising many providers
- `recursive network`: a self-referencing `M:N` / `N:M` pattern, such as user-to-user care, guardian, referral, or collaboration links stored through a relationship table
