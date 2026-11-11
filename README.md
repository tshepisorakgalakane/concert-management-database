# Concert Management Database

A relational database solution for organising the core operations of a concert event. Developed with Oracle SQL, the database manages venue information, stages, artists, event personnel, attendees, tickets, stalls and stall purchases.

## Project overview

The Concert Management Database demonstrates the application of relational database principles to an event-management scenario. It organises related information into structured tables and uses keys and integrity constraints to maintain consistent relationships between records.

### Key features

- Structured relational database schema
- Primary keys and foreign-key relationships
- Data integrity constraints, including required fields, unique values and validation rules
- Sample records for demonstrating database operations
- SQL queries for retrieving information and generating operational summaries
- Entity-relationship documentation

## Database structure

The database consists of nine tables:

| Table | Description |
|---|---|
| `VENUE` | Stores concert venue details. |
| `PARAMEDIC_TEAM` | Stores medical response team information and venue assignments. |
| `STAGE` | Stores stages associated with a venue. |
| `ARTIST` | Stores performer details and stage assignments. |
| `SECURITY_TEAM` | Stores security team information and operational assignments. |
| `STALL` | Stores food, beverage and merchandise stall details. |
| `ATTENDEE` | Stores attendee information. |
| `TICKET` | Stores ticket details and attendee allocations. |
| `STALL_PURCHASE` | Records purchases made by attendees at stalls. |

## Repository structure

```text
concert-management-database/
├── README.md
├── .gitignore
├── sql/
│   ├── 01_create_tables.sql
│   ├── 02_insert_sample_data.sql
│   └── 03_reporting_queries.sql
└── documentation/
    ├── database-overview.md
    └── relationships.md
```

## Getting started

1. Open Oracle SQL Developer and connect to an Oracle Database schema.
2. Execute `sql/01_create_tables.sql` to create the database tables.
3. Execute `sql/02_insert_sample_data.sql` to populate the tables with sample records.
4. Run the required statements in `sql/03_reporting_queries.sql` to explore the database.

Execute the scripts in the order shown above.

## Database design

The schema uses Oracle data types suited to the information being stored. Monetary values use numeric columns, while telephone numbers are stored as text to preserve leading zeroes and international prefixes. Foreign keys establish relationships between tables, while check and unique constraints support data consistency.

The ticket table references the venue through `VENUE_ID`, avoiding duplicated venue-address information. The `STALL_PURCHASE` table uses its own primary key to allow multiple purchase records for the same attendee and stall.

The entity relationships and design assumptions are described in the [database overview](documentation/database-overview.md) and [relationship documentation](documentation/relationships.md).

## Project contribution

This is a collaborative academic project. My contribution focused on the Oracle SQL database implementation and scripting, alongside group members who contributed to the wider database design and project deliverables.

## Technologies

- Oracle Database
- Oracle SQL
- SQL Developer
- Git and GitHub
