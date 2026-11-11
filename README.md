# Concert Management Database

An Oracle SQL relational database project for managing concert operations, including venues, stages, artists, event staff, attendees, tickets, stalls and stall purchases.

> **Project type:** Collaborative academic database project  
> **Platform:** Oracle Database  
> **Status:** Portfolio refinement — SQL scripts still require execution and verification in Oracle SQL Developer.

## Overview

This project demonstrates relational database design, Oracle SQL table creation, primary and foreign keys, data integrity constraints, sample data and reporting queries.

## Database tables

| Table | Purpose |
|---|---|
| VENUE | Concert venue details |
| PARAMEDIC_TEAM | Medical response teams and venue association |
| STAGE | Stages within a venue |
| ARTIST | Performers and stage assignments |
| SECURITY_TEAM | Security teams and optional assignments |
| STALL | Food, drinks and merchandise stalls |
| ATTENDEE | Attendee information |
| TICKET | Ticket details and attendee allocation |
| STALL_PURCHASE | Associative transaction table connecting attendees and stalls |

## Entity-relationship diagram

The diagram in [documentation/relationships.md](documentation/relationships.md) shows the tables and how they relate. GitHub renders the Mermaid diagram directly in that file.

## Repository structure

- sql/01_create_tables.sql — creates the database tables and constraints
- sql/02_insert_sample_data.sql — inserts fictional demonstration records
- sql/03_reporting_queries.sql — example reporting queries
- documentation/database-overview.md — scope, design decisions and assumptions
- documentation/relationships.md — ER diagram and relationship explanation

## Run the project

1. Connect to an Oracle Database schema using Oracle SQL Developer.
2. Run sql/01_create_tables.sql in a clean schema.
3. Run sql/02_insert_sample_data.sql.
4. Run individual queries from sql/03_reporting_queries.sql.

Run the scripts in that order. The creation script does not drop existing tables.

## Design improvements

- Monetary values use NUMBER(10,2), not character columns.
- Telephone numbers use VARCHAR2 to preserve leading zeroes and international prefixes.
- Ticket records reference VENUE_ID instead of duplicating venue addresses.
- Constraints validate required values, supported categories and non-negative prices.
- STALL_PURCHASE has its own identity key so an attendee can make multiple purchases at the same stall.

## Contribution and academic integrity

This is a collaborative academic project. My contribution focused on the Oracle SQL database implementation and scripting, alongside group members who contributed to the wider design and coursework deliverables. This repository presents a refined portfolio version and does not claim sole authorship.

## Validation status

The scripts have been prepared for Oracle SQL, but have **not yet been executed or independently tested in your Oracle environment**. Please run them in order and report any errors so they can be corrected.

## Future improvements

Potential extensions include event scheduling across multiple dates, ticket status and payment records, security shift assignments and medical incident records. These should be added only after the requirements and business rules are agreed.
