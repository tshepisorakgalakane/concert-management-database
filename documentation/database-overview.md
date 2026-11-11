# Database Overview

## Purpose

The Concert Management Database organises information required for the management of a concert event. It provides a structured way to store and retrieve venue, stage, performer, staff, attendee, ticket and stall-purchase information.

## Database scope

The database contains nine related tables:

1. `VENUE`
2. `PARAMEDIC_TEAM`
3. `STAGE`
4. `ARTIST`
5. `SECURITY_TEAM`
6. `STALL`
7. `ATTENDEE`
8. `TICKET`
9. `STALL_PURCHASE`

The `STALL_PURCHASE` table connects attendees and stalls by recording individual purchase transactions.

## Design principles

### Primary and foreign keys

Each table has a primary key that uniquely identifies its records. Foreign keys define relationships between tables and maintain referential integrity.

### Data types

- `VARCHAR2` stores names, descriptions, identifiers and contact numbers.
- `NUMBER(10,2)` stores monetary values.
- `TIMESTAMP` stores purchase date and time information.

Telephone numbers are stored as text because they are identifiers rather than values used in arithmetic calculations.

### Integrity constraints

- `NOT NULL` ensures required fields contain values.
- `UNIQUE` prevents duplicate non-null email addresses within the relevant table.
- `CHECK` constraints restrict selected categories and numeric values.
- Foreign-key constraints ensure referenced parent records exist.

### Venue information

The `TICKET` table stores `VENUE_ID` as a foreign key instead of duplicating the venue address. Venue details can be retrieved through a join with the `VENUE` table.

### Stall purchases

The `STALL_PURCHASE` table uses a generated `PURCHASE_ID` primary key. This allows the same attendee to make multiple purchases at the same stall while keeping each transaction separately identifiable.

## Relationships and business rules

The relationships are illustrated in [relationships.md](relationships.md). The schema includes optional assignments where a record may not yet be associated with another record, such as a ticket that has not been allocated to an attendee.

Security team records can reference a venue, stage and artist. The current structure does not enforce that the selected stage and artist belong to the same venue; this rule can be implemented if required by the project's business rules.

## Further development

Possible extensions include event scheduling, ticket status tracking, payment records, security shift assignments and medical incident records. These additions can be considered as the system's requirements evolve.
