# Database Overview

## Purpose

The Concert Management Database organises core information for a concert event. It stores venue, stage, performer, staff, attendee, ticket and stall-purchase records in related relational tables.

## Scope

The portfolio schema contains nine tables: VENUE, PARAMEDIC_TEAM, STAGE, ARTIST, SECURITY_TEAM, STALL, ATTENDEE, TICKET and STALL_PURCHASE. STALL_PURCHASE is the associative transaction table connecting attendees and stalls.

## Design decisions

- **Keys:** Every table has a primary key. Foreign keys represent relationships and prevent references to missing parent records.
- **Data types:** VARCHAR2 stores text and contact numbers; NUMBER(10,2) stores monetary values; TIMESTAMP records purchase date and time.
- **Validation:** NOT NULL, UNIQUE and CHECK constraints enforce required fields, unique non-null emails and valid categories or numeric values.
- **Venue address:** TICKET stores VENUE_ID rather than duplicating the venue address. The address can be retrieved by joining TICKET to VENUE.
- **Purchases:** STALL_PURCHASE uses an identity-generated PURCHASE_ID. This permits an attendee to make multiple purchases at the same stall.

## Assumptions and limitations

- A venue can contain multiple stages and stalls.
- An artist may be unassigned or assigned to one stage in this model.
- An attendee may be associated with zero or one paramedic team. This relationship is retained from the original coursework concept and should be checked against the group's approved business rules.
- A ticket may be unassigned or assigned to one attendee. An attendee may be associated with multiple tickets.
- Security team venue, stage and artist references are optional. The current schema does not enforce that the selected stage and artist belong to the same venue; that rule would require additional modelling.
- This design does not include event scheduling across multiple dates, payments, refunds, ticket scanning or staff shift history.

## Future development

Possible extensions include an EVENT table, ticket status and payment records, security shift assignments and medical incident records. Add these only after requirements and business rules have been agreed.
