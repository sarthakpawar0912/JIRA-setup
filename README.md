# JIRA Project Management - Complete Setup Guide
# Bus Ticket Booking System

> **Tool:** Atlassian JIRA (Cloud - Free Tier)
> **Admin:** sarthakpawar0912 | **Team Size:** 5 Members | **Duration:** 15 Days
> **Methodology:** Agile Scrum with 3 Sprints (5 days each)

---

## Table of Contents

1. [What is JIRA & Why Your Team Needs It](#1-what-is-jira--why-your-team-needs-it)
2. [Create Atlassian Account & JIRA Project](#2-create-atlassian-account--jira-project)
3. [Add Team Members & Set Roles](#3-add-team-members--set-roles)
4. [Configure the Board](#4-configure-the-board)
5. [Create Epics (Big Features)](#5-create-epics-big-features)
6. [Create User Stories](#6-create-user-stories)
7. [Break Stories into Tasks & Sub-Tasks](#7-break-stories-into-tasks--sub-tasks)
8. [Sprint Planning - 3 Sprints for 15 Days](#8-sprint-planning---3-sprints-for-15-days)
9. [Complete Ticket List (All 100+ Tickets)](#9-complete-ticket-list-all-100-tickets)
10. [Workflow Customization](#10-workflow-customization)
11. [Labels, Components & Filters](#11-labels-components--filters)
12. [How Each Member Uses JIRA Daily](#12-how-each-member-uses-jira-daily)
13. [GitHub + JIRA Integration](#13-github--jira-integration)
14. [JIRA Dashboard & Reports](#14-jira-dashboard--reports)
15. [Best Practices for Your Team](#15-best-practices-for-your-team)

---

## 1. What is JIRA & Why Your Team Needs It

### What JIRA Does

```
Without JIRA:
  "Hey who is working on payments?"
  "Is the booking API done?"
  "What should I do next?"
  "We forgot to build the review feature!"

With JIRA:
  Every task is a TICKET with:
    - Clear title and description
    - Assigned to ONE person
    - Status: To Do / In Progress / Done
    - Priority: Highest / High / Medium / Low
    - Sprint deadline
    - Linked to GitHub branch and PR
```

### JIRA Hierarchy

```
PROJECT: Bus Ticket Booking (BTB)
  |
  +-- EPIC: Agency & Bus Management (big feature area)
  |     |
  |     +-- STORY: As an admin, I can add a new agency
  |     |     |
  |     |     +-- TASK: Create Agency entity class
  |     |     +-- TASK: Create AgencyRepository
  |     |     +-- TASK: Create AgencyService
  |     |     +-- TASK: Create AgencyController
  |     |     +-- TASK: Create agency-add.html Thymeleaf page
  |     |     +-- TASK: Write unit tests for AgencyService
  |     |
  |     +-- STORY: As a user, I can search buses by route
  |           |
  |           +-- TASK: Create search API endpoint
  |           +-- TASK: Create search-results.html page
  |
  +-- EPIC: Booking System
  |     |
  |     +-- STORY: As a customer, I can book a seat
  |           +-- TASK: ...
  |
  +-- EPIC: Payment System
        +-- STORY: ...
```

### Key Terminology

| Term | Meaning | Example |
|------|---------|---------|
| **Epic** | A large feature area that takes multiple sprints | "Agency & Bus Management" |
| **Story** | A user-facing feature described from user's perspective | "As a customer, I can search buses" |
| **Task** | A technical work item, usually part of a story | "Create BusRepository.java" |
| **Sub-task** | A smaller piece of a task | "Add findByType() method to BusRepository" |
| **Bug** | Something broken that needs fixing | "Booking fails when seats = 0" |
| **Sprint** | A fixed time period (5 days for your project) | Sprint 1: Apr 9 - Apr 13 |
| **Backlog** | All tickets not yet assigned to a sprint | Unplanned work |
| **Board** | Visual view of current sprint's tickets | Kanban/Scrum board |
| **Story Points** | Effort estimate (1=tiny, 2=small, 3=medium, 5=large, 8=huge) | "Create CRUD API" = 3 points |

---

## 2. Create Atlassian Account & JIRA Project

### Step 2.1: Sign Up for Atlassian Cloud (Free)

1. Go to **https://www.atlassian.com/software/jira/free**
2. Click **Get it free**
3. Sign up with your email (use the same email as your GitHub)
4. Create a site:
   ```
   Site name: busbooking
   Your URL will be: https://busbooking.atlassian.net
   ```
5. Select **JIRA Software** (not JIRA Service Management)
6. Choose the **Free plan** (up to 10 users - perfect for your team of 5)

### Step 2.2: Create the Project

1. After setup, you'll land on the JIRA dashboard
2. Click **Projects** -> **Create project**
3. Select **Scrum** (not Kanban - Scrum has sprints which you need)
4. Fill in:
   ```
   Name:     Bus Ticket Booking
   Key:      BTB
   Type:     Team-managed project (simpler) OR Company-managed (more control)
   Lead:     You (sarthakpawar0912)
   ```
5. Click **Create**

Your project key is **BTB**. All tickets will be: BTB-1, BTB-2, BTB-3, etc.

### Step 2.3: Choose Team-Managed vs Company-Managed

| Feature | Team-Managed | Company-Managed |
|---------|-------------|-----------------|
| Setup | Simpler, faster | More configuration options |
| Workflow | Basic (To Do, In Progress, Done) | Fully customizable |
| Permissions | Simple | Granular per-role |
| Best for | Small teams, college projects | Enterprise, strict processes |

**Recommendation:** Start with **Team-managed**. You can always migrate later.

---

## 3. Add Team Members & Set Roles

### Step 3.1: Invite Team Members

1. Go to **https://busbooking.atlassian.net**
2. Click the **gear icon** (top right) -> **User management**
   - Or go to **admin.atlassian.com** -> **Directory** -> **Users**
3. Click **Invite users**
4. Enter email addresses of all 4 team members
5. Click **Invite**

They'll receive an email invitation to join your Atlassian site.

### Step 3.2: Assign Project Roles

1. Go to **Project Settings** (bottom-left gear in your project)
2. Click **Access** (or **People**)
3. Add each member with their role:

```
sarthakpawar0912     -> Role: Administrator
Member 2 (Agency)    -> Role: Member
Member 3 (Booking)   -> Role: Member
Member 4 (Payment)   -> Role: Member
Member 5 (Frontend)  -> Role: Member
```

### Step 3.3: Understand Roles

| Role | Can Do | Who |
|------|--------|-----|
| **Administrator** | Everything: create sprints, manage board, edit workflows, delete tickets, manage members | You (Sarthak) |
| **Member** | Create tickets, edit their tickets, move tickets, add comments, log work | Members 2-5 |
| **Viewer** | Only view tickets and board (read-only) | External stakeholders, professors |

---

## 4. Configure the Board

### Step 4.1: Set Up Board Columns

1. Go to your project **Board** view
2. Click the **three dots** (top right) -> **Board settings** OR **Configure board**
3. Under **Columns**, set up:

```
Column 1: BACKLOG        (gray)    - Not started, waiting to be picked up
Column 2: TO DO          (blue)    - Assigned, ready to start
Column 3: IN PROGRESS    (yellow)  - Currently being worked on
Column 4: CODE REVIEW    (orange)  - PR created, waiting for review
Column 5: TESTING        (purple)  - Being tested
Column 6: DONE           (green)   - Completed and merged
```

To add a new column:
- Click **+ Add column** (or drag and drop)
- Name it and assign a status

### Step 4.2: Map Statuses to Columns

```
BACKLOG column     <- Status: Backlog
TO DO column       <- Status: To Do, Selected for Development
IN PROGRESS column <- Status: In Progress
CODE REVIEW column <- Status: In Review
TESTING column     <- Status: Testing, QA
DONE column        <- Status: Done
```

### Step 4.3: Set WIP (Work in Progress) Limits

This prevents team members from taking on too much work:

1. In Board settings -> Columns
2. Set maximum for each column:

```
BACKLOG:      No limit
TO DO:        10
IN PROGRESS:  5 (max 1 per person)
CODE REVIEW:  3
TESTING:      3
DONE:         No limit
```

---

## 5. Create Epics (Big Features)

### Step 5.1: Create Epics

1. Go to **Backlog** view (left sidebar)
2. Click **+ Create Epic** (or create issue with type = Epic)

Create these 8 Epics:

```
EPIC 1: BTB-1  | Project Setup & Infrastructure
  Summary:     Project scaffolding, CI/CD, Docker, SonarQube
  Color:       Gray
  Assignee:    Member 1 (Admin)
  Priority:    Highest

EPIC 2: BTB-2  | User Authentication & Security
  Summary:     Registration, login, JWT, Spring Security, roles
  Color:       Red
  Assignee:    Member 1 (Admin)
  Priority:    Highest

EPIC 3: BTB-3  | Agency & Bus Management
  Summary:     Agency CRUD, bus CRUD, driver management, route management
  Color:       Blue
  Assignee:    Member 2
  Priority:    High

EPIC 4: BTB-4  | Trip & Schedule Management
  Summary:     Trip CRUD, schedule management, seat availability
  Color:       Cyan
  Assignee:    Member 3
  Priority:    High

EPIC 5: BTB-5  | Booking System
  Summary:     Seat selection, booking flow, cancellation, e-ticket
  Color:       Green
  Assignee:    Member 3
  Priority:    High

EPIC 6: BTB-6  | Payment System
  Summary:     Payment processing, refunds, payment history
  Color:       Yellow
  Assignee:    Member 4
  Priority:    High

EPIC 7: BTB-7  | Frontend (Thymeleaf)
  Summary:     All Thymeleaf pages, UI/UX, responsive design
  Color:       Purple
  Assignee:    Member 5
  Priority:    High

EPIC 8: BTB-8  | Deployment & DevOps
  Summary:     Docker, cloud deployment, SonarQube, monitoring
  Color:       Orange
  Assignee:    Member 1 (Admin)
  Priority:    Medium
```

---

## 6. Create User Stories

### How to Write a Good User Story

```
Format:   As a [role], I want to [action] so that [benefit]
Example:  As a customer, I want to search buses by route and date so that I can find available trips

Acceptance Criteria (AC):
  GIVEN I am on the home page
  WHEN I enter source city, destination city, and travel date
  AND I click "Search Buses"
  THEN I see a list of available buses with departure time, price, and available seats
```

### Create These User Stories

**Epic 1: Project Setup & Infrastructure**

```
BTB-9   As a developer, I want the Spring Boot project initialized with all dependencies
        AC: Project runs with `mvn spring-boot:run`, connects to MySQL
        Story Points: 3 | Assignee: Member 1

BTB-10  As a developer, I want a .gitignore and branch strategy configured
        AC: main and develop branches exist, .gitignore excludes IDE/secret files
        Story Points: 1 | Assignee: Member 1

BTB-11  As a developer, I want the database schema loaded with seed data
        AC: All 10 tables created, seed data inserted, all FKs working
        Story Points: 2 | Assignee: Member 1

BTB-12  As a developer, I want Docker Compose for local development
        AC: `docker-compose up` starts MySQL + app, app connects to DB
        Story Points: 3 | Assignee: Member 1

BTB-13  As a developer, I want SonarQube configured for code analysis
        AC: `mvn sonar:sonar` runs successfully, results visible on dashboard
        Story Points: 3 | Assignee: Member 1
```

**Epic 2: User Authentication & Security**

```
BTB-14  As a customer, I want to register an account
        AC: Register with name, email, phone, password. Email must be unique.
            Password stored as BCrypt hash. Validation errors shown on form.
        Story Points: 5 | Assignee: Member 1

BTB-15  As a customer, I want to login with email and password
        AC: JWT token generated on success. Invalid credentials show error.
            Token stored in session/cookie for Thymeleaf.
        Story Points: 5 | Assignee: Member 1

BTB-16  As a customer, I want to logout
        AC: Session/token invalidated. Redirected to home page.
        Story Points: 2 | Assignee: Member 1

BTB-17  As an admin, I want role-based access control
        AC: CUSTOMER, AGENCY_ADMIN, SYSTEM_ADMIN roles enforced.
            Unauthorized access returns 403.
        Story Points: 5 | Assignee: Member 1

BTB-18  As a customer, I want to view and edit my profile
        AC: Can view name, email, phone, address. Can update all fields.
        Story Points: 3 | Assignee: Member 1
```

**Epic 3: Agency & Bus Management**

```
BTB-19  As an admin, I want to view all agencies
        AC: Paginated list showing name, contact person, email, phone.
            Search by name works.
        Story Points: 3 | Assignee: Member 2

BTB-20  As an admin, I want to add a new agency
        AC: Form with name, contact person, email, phone. Validates required fields.
            Shows success message after creation.
        Story Points: 3 | Assignee: Member 2

BTB-21  As an admin, I want to edit and delete an agency
        AC: Edit form pre-filled with current data. Delete shows confirmation.
            Can't delete agency that has active buses/offices.
        Story Points: 3 | Assignee: Member 2

BTB-22  As an admin, I want to manage agency offices
        AC: CRUD for offices under an agency. Each office has address, contact, email.
        Story Points: 3 | Assignee: Member 2

BTB-23  As an agency admin, I want to add a new bus
        AC: Form with registration number, capacity, type (Seater/AC Sleeper/etc), 
            assigned to an office. Registration number must be unique.
        Story Points: 3 | Assignee: Member 2

BTB-24  As an agency admin, I want to view all buses in my agency
        AC: List shows bus number, type, capacity, office location. Filter by type.
        Story Points: 2 | Assignee: Member 2

BTB-25  As an agency admin, I want to edit and delete a bus
        AC: Can't delete a bus that has upcoming trips.
        Story Points: 2 | Assignee: Member 2

BTB-26  As an admin, I want to manage drivers
        AC: CRUD for drivers. Each driver has name, license, phone, assigned office.
        Story Points: 3 | Assignee: Member 2

BTB-27  As an admin, I want to manage routes
        AC: CRUD for routes. Each route has from_city, to_city, break_points, duration.
        Story Points: 3 | Assignee: Member 2

BTB-28  As a user, I want to view all available routes
        AC: List of routes with from/to cities, duration, and number of trips on each route.
        Story Points: 2 | Assignee: Member 2
```

**Epic 4: Trip & Schedule Management**

```
BTB-29  As an agency admin, I want to create a trip
        AC: Select route, bus, boarding/dropping addresses, departure/arrival time,
            both drivers, set fare. Available seats auto-set from bus capacity.
        Story Points: 5 | Assignee: Member 3

BTB-30  As an agency admin, I want to view all trips for my agency
        AC: List with route, date, bus, departure time, available seats, fare.
            Filter by date and route.
        Story Points: 3 | Assignee: Member 3

BTB-31  As an agency admin, I want to edit and cancel a trip
        AC: Can edit future trips only. Cancelling a trip refunds all bookings.
        Story Points: 3 | Assignee: Member 3

BTB-32  As a customer, I want to search trips by source and destination
        AC: Enter from_city, to_city, date. See matching trips with bus type,
            departure time, fare, available seats. Sort by price/time.
        Story Points: 5 | Assignee: Member 3

BTB-33  As a customer, I want to see trip details
        AC: Shows full route, boarding/dropping points, bus details, driver info,
            amenities, and seat availability count.
        Story Points: 3 | Assignee: Member 3

BTB-34  As a customer, I want to see seat availability for a trip
        AC: Shows total seats vs booked seats. List of available seat numbers.
        Story Points: 3 | Assignee: Member 3
```

**Epic 5: Booking System**

```
BTB-35  As a customer, I want to select a seat and book it
        AC: See available seats for a trip. Select one seat. Enter passenger name.
            Seat marked as "Booked" after booking. Available seats count decremented.
        Story Points: 8 | Assignee: Member 3

BTB-36  As a customer, I want to view my bookings
        AC: List of all bookings with trip details, seat number, status, date.
            Filter by upcoming/past.
        Story Points: 3 | Assignee: Member 3

BTB-37  As a customer, I want to view a single booking detail
        AC: Shows trip route, bus info, seat number, fare paid, booking status,
            boarding/dropping address.
        Story Points: 2 | Assignee: Member 3

BTB-38  As a customer, I want to cancel my booking
        AC: Only upcoming bookings can be cancelled. Seat status changed to "Available".
            Available seats count incremented. Refund initiated.
        Story Points: 5 | Assignee: Member 3

BTB-39  As a customer, I want to receive a booking confirmation
        AC: After successful booking + payment, show confirmation page with
            booking ID, trip details, seat number, amount paid.
        Story Points: 3 | Assignee: Member 3

BTB-40  As an admin, I want to view all bookings across agencies
        AC: Admin dashboard shows all bookings. Filter by agency, date, status.
        Story Points: 3 | Assignee: Member 3
```

**Epic 6: Payment System**

```
BTB-41  As a customer, I want to pay for my booking
        AC: After seat selection, redirected to payment page. Shows amount.
            Simulated payment (for now). On success, booking confirmed.
        Story Points: 5 | Assignee: Member 4

BTB-42  As a customer, I want to see payment confirmation
        AC: After successful payment, shows payment ID, amount, date, status.
        Story Points: 2 | Assignee: Member 4

BTB-43  As a customer, I want to receive a refund on cancellation
        AC: When booking cancelled, payment status updated. Refund amount shown
            to customer. (Simulated refund for now.)
        Story Points: 5 | Assignee: Member 4

BTB-44  As a customer, I want to view my payment history
        AC: List of all payments with booking ID, amount, date, status (Success/Failed).
        Story Points: 3 | Assignee: Member 4

BTB-45  As an admin, I want to view all payments
        AC: Admin can see all payments. Filter by date, status, agency.
            Shows total revenue.
        Story Points: 3 | Assignee: Member 4

BTB-46  As a customer, I want payment failure handled gracefully
        AC: If payment fails, booking stays in "Available" status.
            Customer can retry payment. Error message shown.
        Story Points: 3 | Assignee: Member 4
```

**Epic 7: Frontend (Thymeleaf)**

```
BTB-47  As a user, I want a clean and responsive home page
        AC: Shows search form (from, to, date), popular routes, header, footer.
            Works on mobile and desktop.
        Story Points: 5 | Assignee: Member 5

BTB-48  As a user, I want a registration page
        AC: Form with name, email, phone, password, confirm password.
            Client-side + server-side validation. Error messages shown.
        Story Points: 3 | Assignee: Member 5

BTB-49  As a user, I want a login page
        AC: Email + password form. "Forgot password" link. Error on invalid login.
        Story Points: 3 | Assignee: Member 5

BTB-50  As a customer, I want a search results page
        AC: Shows matching trips in card format. Each card: bus name, type,
            departure, arrival, duration, fare, available seats, "Book Now" button.
            Sort and filter options.
        Story Points: 5 | Assignee: Member 5

BTB-51  As a customer, I want a seat selection page
        AC: Visual seat layout. Click to select. Selected seat highlighted.
            Shows price. "Continue" button.
        Story Points: 8 | Assignee: Member 5

BTB-52  As a customer, I want a booking confirmation page
        AC: Shows booking ID, trip details, seat, amount. "Download Ticket" button.
            "View My Bookings" link.
        Story Points: 3 | Assignee: Member 5

BTB-53  As a customer, I want a "My Bookings" page
        AC: Table/cards of all bookings. Status badges (Booked/Cancelled).
            "Cancel" button for upcoming bookings.
        Story Points: 3 | Assignee: Member 5

BTB-54  As a customer, I want a payment page
        AC: Shows booking summary + amount. Payment method selection (simulated).
            "Pay Now" button. Loading state during processing.
        Story Points: 5 | Assignee: Member 5

BTB-55  As an admin, I want an admin dashboard page
        AC: Shows total bookings, revenue, active trips, agency count.
            Links to manage sections.
        Story Points: 5 | Assignee: Member 5

BTB-56  As a customer, I want a profile page
        AC: Shows user info. "Edit" button opens editable form.
        Story Points: 3 | Assignee: Member 5

BTB-57  As a user, I want proper error pages (404, 500)
        AC: Custom 404 and 500 pages with navigation back to home.
        Story Points: 1 | Assignee: Member 5

BTB-58  As a user, I want a common navigation bar and footer
        AC: Navbar with logo, home, search, login/register (guest) or 
            my bookings/profile/logout (logged in). Footer with links.
        Story Points: 3 | Assignee: Member 5
```

**Epic 8: Deployment & DevOps**

```
BTB-59  As a developer, I want Dockerfiles for the application
        AC: Multi-stage Dockerfile. `docker build` succeeds. Image < 200MB.
        Story Points: 3 | Assignee: Member 1

BTB-60  As a developer, I want GitHub Actions CI pipeline
        AC: On every PR: build, test, SonarQube scan. Status shown on PR.
        Story Points: 5 | Assignee: Member 1

BTB-61  As a developer, I want the app deployed to cloud
        AC: App accessible via public URL. Connected to cloud MySQL.
        Story Points: 5 | Assignee: Member 1

BTB-62  As a developer, I want a README with setup instructions
        AC: README has: prerequisites, setup steps, running locally, running with Docker,
            team members, tech stack.
        Story Points: 2 | Assignee: Member 1
```

---

## 7. Break Stories into Tasks & Sub-Tasks

### Example: BTB-35 "Book a Seat" broken into Tasks

```
BTB-35: As a customer, I want to select a seat and book it (STORY - 8 points)
  |
  +-- BTB-63: Create Booking entity mapped to bookings table (TASK - 1 pt)
  |     Assignee: Member 3
  |     Description: JPA entity with trip_id, seat_number, status enum (Available/Booked)
  |
  +-- BTB-64: Create BookingRepository with custom queries (TASK - 1 pt)
  |     Assignee: Member 3
  |     Description: findByTripId, findByTripIdAndSeatNumber, 
  |                  countByTripIdAndStatus, findAvailableSeatsByTripId
  |
  +-- BTB-65: Create BookingService with booking logic (TASK - 3 pt)
  |     Assignee: Member 3
  |     Description:
  |       - Check seat is Available for given trip
  |       - Change seat status to Booked
  |       - Decrement available_seats in trips table
  |       - Return booking details
  |       - Handle concurrent booking (pessimistic lock or optimistic retry)
  |
  +-- BTB-66: Create BookingController REST API (TASK - 2 pt)
  |     Assignee: Member 3
  |     Description:
  |       - POST /api/bookings (create booking)
  |       - GET /api/bookings/{id} (get booking detail)
  |       - GET /api/bookings/customer/{customerId} (my bookings)
  |       - PUT /api/bookings/{id}/cancel (cancel)
  |
  +-- BTB-67: Write unit tests for BookingService (TASK - 2 pt)
  |     Assignee: Member 3
  |     Description:
  |       - Test successful booking
  |       - Test booking already booked seat (should fail)
  |       - Test booking on non-existent trip
  |       - Test cancellation
  |       - Test available seats decrement
  |
  +-- BTB-68: Create seat selection Thymeleaf page (TASK - 3 pt)
        Assignee: Member 5
        Description: Visual seat grid, click to select, show price, continue button
```

### Example: BTB-41 "Payment" broken into Tasks

```
BTB-41: As a customer, I want to pay for my booking (STORY - 5 points)
  |
  +-- BTB-69: Create Payment entity mapped to payments table (TASK - 1 pt)
  |     Assignee: Member 4
  |
  +-- BTB-70: Create PaymentRepository (TASK - 1 pt)
  |     Assignee: Member 4
  |     Description: findByBookingId, findByCustomerId, findByPaymentStatus
  |
  +-- BTB-71: Create PaymentService with payment logic (TASK - 3 pt)
  |     Assignee: Member 4
  |     Description:
  |       - Accept booking ID and customer ID
  |       - Fetch fare from booking's trip
  |       - Simulate payment processing (random success/fail for demo)
  |       - On success: set payment_status = "Success", set payment_date
  |       - On fail: set payment_status = "Failed", release booking
  |       - Return payment receipt
  |
  +-- BTB-72: Create PaymentController REST API (TASK - 2 pt)
  |     Assignee: Member 4
  |     Description:
  |       - POST /api/payments (initiate payment)
  |       - GET /api/payments/{id} (payment status)
  |       - GET /api/payments/customer/{customerId} (payment history)
  |
  +-- BTB-73: Write unit tests for PaymentService (TASK - 2 pt)
  |     Assignee: Member 4
  |
  +-- BTB-74: Create payment checkout Thymeleaf page (TASK - 3 pt)
        Assignee: Member 5
```

### How to Create Tasks in JIRA

1. Open the parent Story (e.g., BTB-35)
2. Click **Create sub-task** (or link a new task to the story)
3. Fill in:
   ```
   Issue Type:    Task (or Sub-task)
   Summary:       Create BookingService with booking logic
   Description:   (detailed description from above)
   Assignee:      Member 3
   Story Points:  3
   Sprint:        Sprint 2
   Epic Link:     BTB-5 (Booking System)
   Labels:        backend, service-layer
   Priority:      High
   ```

---

## 8. Sprint Planning - 3 Sprints for 15 Days

### Sprint Overview

```
Sprint 1: FOUNDATION          (Day 1-5)    Apr 9 - Apr 13
Sprint 2: CORE FEATURES       (Day 6-10)   Apr 14 - Apr 18
Sprint 3: INTEGRATION & DEPLOY(Day 11-15)  Apr 19 - Apr 23
```

### Step 8.1: Create Sprints in JIRA

1. Go to **Backlog** view
2. Click **Create Sprint** at the top
3. Name: `Sprint 1 - Foundation`
4. Start date: `2026-04-09`
5. End date: `2026-04-13`
6. Goal: `Project setup, entities, repositories, basic CRUD APIs, auth system`

Repeat for Sprint 2 and 3.

### Sprint 1: FOUNDATION (Day 1-5)

**Goal:** Project compiles, DB connected, all entities mapped, basic CRUD APIs working, auth system functional.

**Story Points Target: ~50 points across 5 members (10 pts/person)**

```
Ticket    | Summary                                 | Assignee  | Points | Priority
----------+-----------------------------------------+-----------+--------+---------
BTB-9     | Initialize Spring Boot project           | Member 1  | 3      | Highest
BTB-10    | Git setup, .gitignore, branch strategy   | Member 1  | 1      | Highest
BTB-11    | Database schema + seed data loaded        | Member 1  | 2      | Highest
BTB-14    | Customer registration                     | Member 1  | 5      | Highest
BTB-15    | Customer login with JWT                   | Member 1  | 5      | Highest
          |                                           |           |        |
BTB-63    | Agency entity + repository                | Member 2  | 2      | High
BTB-19    | View all agencies API                     | Member 2  | 3      | High
BTB-20    | Add agency API + form                     | Member 2  | 3      | High
BTB-23    | Add bus API + entity                      | Member 2  | 3      | High
BTB-27    | Route CRUD API + entity                   | Member 2  | 3      | High
          |                                           |           |        |
BTB-64    | Booking entity + repository               | Member 3  | 2      | High
BTB-29    | Create trip entity + API                  | Member 3  | 5      | High
BTB-32    | Search trips API (basic)                  | Member 3  | 5      | High
          |                                           |           |        |
BTB-69    | Payment entity + repository               | Member 4  | 2      | High
BTB-70    | PaymentRepository custom queries          | Member 4  | 1      | High
BTB-71    | PaymentService (simulated)                | Member 4  | 3      | High
BTB-72    | PaymentController REST API                | Member 4  | 2      | High
BTB-44    | Payment history API                       | Member 4  | 3      | Medium
          |                                           |           |        |
BTB-58    | Navbar + footer fragments                 | Member 5  | 3      | Highest
BTB-47    | Home page with search form                | Member 5  | 5      | Highest
BTB-48    | Registration page                         | Member 5  | 3      | High
BTB-49    | Login page                                | Member 5  | 3      | High
```

### Sprint 2: CORE FEATURES (Day 6-10)

**Goal:** Full booking flow working end-to-end. Search -> Select Seat -> Book -> Pay -> Confirmation.

```
Ticket    | Summary                                 | Assignee  | Points | Priority
----------+-----------------------------------------+-----------+--------+---------
BTB-16    | Logout functionality                     | Member 1  | 2      | High
BTB-17    | Role-based access control                | Member 1  | 5      | Highest
BTB-18    | Profile view/edit                         | Member 1  | 3      | Medium
BTB-12    | Docker Compose for local dev              | Member 1  | 3      | High
          |                                           |           |        |
BTB-21    | Edit/delete agency                        | Member 2  | 3      | Medium
BTB-22    | Agency office management                  | Member 2  | 3      | Medium
BTB-24    | View buses by agency                      | Member 2  | 2      | Medium
BTB-25    | Edit/delete bus                           | Member 2  | 2      | Medium
BTB-26    | Driver CRUD                               | Member 2  | 3      | Medium
BTB-28    | View all routes (public)                  | Member 2  | 2      | Medium
          |                                           |           |        |
BTB-65    | BookingService with full logic            | Member 3  | 3      | Highest
BTB-66    | BookingController REST API                | Member 3  | 2      | Highest
BTB-35    | Complete seat selection + booking flow    | Member 3  | 8      | Highest
BTB-34    | Seat availability API                     | Member 3  | 3      | High
          |                                           |           |        |
BTB-41    | Payment processing flow                   | Member 4  | 5      | Highest
BTB-42    | Payment confirmation page                 | Member 4  | 2      | High
BTB-43    | Refund on cancellation                    | Member 4  | 5      | High
BTB-46    | Payment failure handling                  | Member 4  | 3      | High
          |                                           |           |        |
BTB-50    | Search results page                       | Member 5  | 5      | Highest
BTB-51    | Seat selection page (visual grid)         | Member 5  | 8      | Highest
BTB-54    | Payment checkout page                     | Member 5  | 5      | High
BTB-52    | Booking confirmation page                 | Member 5  | 3      | High
```

### Sprint 3: INTEGRATION & DEPLOY (Day 11-15)

**Goal:** End-to-end flow tested, bugs fixed, deployed to cloud, demo ready.

```
Ticket    | Summary                                 | Assignee  | Points | Priority
----------+-----------------------------------------+-----------+--------+---------
BTB-13    | SonarQube setup + first scan             | Member 1  | 3      | High
BTB-59    | Dockerfiles for application              | Member 1  | 3      | Highest
BTB-60    | GitHub Actions CI pipeline               | Member 1  | 5      | Highest
BTB-61    | Deploy to cloud                           | Member 1  | 5      | Highest
BTB-62    | README with setup instructions            | Member 1  | 2      | Medium
          |                                           |           |        |
BTB-67    | Unit tests for BookingService             | Member 2  | 2      | High
BTB-73    | Unit tests for PaymentService             | Member 4  | 2      | High
          |                                           |           |        |
BTB-36    | My bookings page (data)                   | Member 3  | 3      | High
BTB-37    | Booking detail page (data)                | Member 3  | 2      | Medium
BTB-38    | Cancel booking flow                       | Member 3  | 5      | High
BTB-39    | Booking confirmation with receipt          | Member 3  | 3      | Medium
BTB-40    | Admin: view all bookings                  | Member 3  | 3      | Medium
          |                                           |           |        |
BTB-45    | Admin: view all payments                  | Member 4  | 3      | Medium
          |                                           |           |        |
BTB-53    | My Bookings page (UI)                     | Member 5  | 3      | High
BTB-55    | Admin dashboard page                      | Member 5  | 5      | High
BTB-56    | Profile page                              | Member 5  | 3      | Medium
BTB-57    | Error pages (404, 500)                    | Member 5  | 1      | Low
          |                                           |           |        |
BTB-75    | End-to-end testing                        | ALL       | 5      | Highest
BTB-76    | Bug fixes from testing                    | ALL       | 5      | Highest
BTB-77    | SonarQube issue cleanup                   | ALL       | 3      | High
BTB-78    | Demo preparation                          | ALL       | 2      | Highest
```

### Step 8.2: Start a Sprint

1. Go to **Backlog**
2. Drag tickets into "Sprint 1" section
3. Click **Start Sprint**
4. Confirm the start and end dates
5. The sprint is now active and visible on the Board

---

## 9. Complete Ticket List (All 100+ Tickets)

### Quick-Create Template

Here's a CSV-style format you can use to bulk-create tickets:

```
Type     | Key    | Summary                                    | Epic   | Assignee | SP | Sprint  | Priority
---------+--------+--------------------------------------------+--------+----------+----+---------+---------
Epic     | BTB-1  | Project Setup & Infrastructure             | -      | Mem 1    | -  | -       | Highest
Epic     | BTB-2  | User Authentication & Security             | -      | Mem 1    | -  | -       | Highest
Epic     | BTB-3  | Agency & Bus Management                    | -      | Mem 2    | -  | -       | High
Epic     | BTB-4  | Trip & Schedule Management                 | -      | Mem 3    | -  | -       | High
Epic     | BTB-5  | Booking System                             | -      | Mem 3    | -  | -       | High
Epic     | BTB-6  | Payment System                             | -      | Mem 4    | -  | -       | High
Epic     | BTB-7  | Frontend (Thymeleaf)                       | -      | Mem 5    | -  | -       | High
Epic     | BTB-8  | Deployment & DevOps                        | -      | Mem 1    | -  | -       | Medium
         |        |                                            |        |          |    |         |
Story    | BTB-9  | Initialize Spring Boot project             | BTB-1  | Mem 1    | 3  | Sp 1    | Highest
Story    | BTB-10 | Git + branch strategy                      | BTB-1  | Mem 1    | 1  | Sp 1    | Highest
Story    | BTB-11 | DB schema + seed data                      | BTB-1  | Mem 1    | 2  | Sp 1    | Highest
Story    | BTB-12 | Docker Compose local dev                   | BTB-1  | Mem 1    | 3  | Sp 2    | High
Story    | BTB-13 | SonarQube setup                            | BTB-1  | Mem 1    | 3  | Sp 3    | High
Story    | BTB-14 | Customer registration                      | BTB-2  | Mem 1    | 5  | Sp 1    | Highest
Story    | BTB-15 | Customer login + JWT                       | BTB-2  | Mem 1    | 5  | Sp 1    | Highest
Story    | BTB-16 | Logout                                     | BTB-2  | Mem 1    | 2  | Sp 2    | High
Story    | BTB-17 | Role-based access control                  | BTB-2  | Mem 1    | 5  | Sp 2    | Highest
Story    | BTB-18 | Profile view/edit                          | BTB-2  | Mem 1    | 3  | Sp 2    | Medium
Story    | BTB-19 | View all agencies                          | BTB-3  | Mem 2    | 3  | Sp 1    | High
Story    | BTB-20 | Add new agency                             | BTB-3  | Mem 2    | 3  | Sp 1    | High
Story    | BTB-21 | Edit/delete agency                         | BTB-3  | Mem 2    | 3  | Sp 2    | Medium
Story    | BTB-22 | Agency office management                   | BTB-3  | Mem 2    | 3  | Sp 2    | Medium
Story    | BTB-23 | Add new bus                                | BTB-3  | Mem 2    | 3  | Sp 1    | High
Story    | BTB-24 | View buses by agency                       | BTB-3  | Mem 2    | 2  | Sp 2    | Medium
Story    | BTB-25 | Edit/delete bus                            | BTB-3  | Mem 2    | 2  | Sp 2    | Medium
Story    | BTB-26 | Driver CRUD                                | BTB-3  | Mem 2    | 3  | Sp 2    | Medium
Story    | BTB-27 | Route CRUD                                 | BTB-3  | Mem 2    | 3  | Sp 1    | High
Story    | BTB-28 | View routes (public)                       | BTB-3  | Mem 2    | 2  | Sp 2    | Medium
Story    | BTB-29 | Create trip                                | BTB-4  | Mem 3    | 5  | Sp 1    | High
Story    | BTB-30 | View trips (agency admin)                  | BTB-4  | Mem 3    | 3  | Sp 2    | Medium
Story    | BTB-31 | Edit/cancel trip                           | BTB-4  | Mem 3    | 3  | Sp 2    | Medium
Story    | BTB-32 | Search trips by route                      | BTB-4  | Mem 3    | 5  | Sp 1    | High
Story    | BTB-33 | Trip detail page                           | BTB-4  | Mem 3    | 3  | Sp 2    | Medium
Story    | BTB-34 | Seat availability                          | BTB-4  | Mem 3    | 3  | Sp 2    | High
Story    | BTB-35 | Book a seat                                | BTB-5  | Mem 3    | 8  | Sp 2    | Highest
Story    | BTB-36 | My bookings                                | BTB-5  | Mem 3    | 3  | Sp 3    | High
Story    | BTB-37 | Booking detail                             | BTB-5  | Mem 3    | 2  | Sp 3    | Medium
Story    | BTB-38 | Cancel booking                             | BTB-5  | Mem 3    | 5  | Sp 3    | High
Story    | BTB-39 | Booking confirmation                       | BTB-5  | Mem 3    | 3  | Sp 3    | Medium
Story    | BTB-40 | Admin view all bookings                    | BTB-5  | Mem 3    | 3  | Sp 3    | Medium
Story    | BTB-41 | Pay for booking                            | BTB-6  | Mem 4    | 5  | Sp 2    | Highest
Story    | BTB-42 | Payment confirmation                       | BTB-6  | Mem 4    | 2  | Sp 2    | High
Story    | BTB-43 | Refund on cancellation                     | BTB-6  | Mem 4    | 5  | Sp 2    | High
Story    | BTB-44 | Payment history                            | BTB-6  | Mem 4    | 3  | Sp 1    | Medium
Story    | BTB-45 | Admin view all payments                    | BTB-6  | Mem 4    | 3  | Sp 3    | Medium
Story    | BTB-46 | Payment failure handling                   | BTB-6  | Mem 4    | 3  | Sp 2    | High
Story    | BTB-47 | Home page + search form                    | BTB-7  | Mem 5    | 5  | Sp 1    | Highest
Story    | BTB-48 | Registration page                          | BTB-7  | Mem 5    | 3  | Sp 1    | High
Story    | BTB-49 | Login page                                 | BTB-7  | Mem 5    | 3  | Sp 1    | High
Story    | BTB-50 | Search results page                        | BTB-7  | Mem 5    | 5  | Sp 2    | Highest
Story    | BTB-51 | Seat selection page                        | BTB-7  | Mem 5    | 8  | Sp 2    | Highest
Story    | BTB-52 | Booking confirmation page                  | BTB-7  | Mem 5    | 3  | Sp 2    | High
Story    | BTB-53 | My Bookings page                           | BTB-7  | Mem 5    | 3  | Sp 3    | High
Story    | BTB-54 | Payment checkout page                      | BTB-7  | Mem 5    | 5  | Sp 2    | High
Story    | BTB-55 | Admin dashboard                            | BTB-7  | Mem 5    | 5  | Sp 3    | High
Story    | BTB-56 | Profile page                               | BTB-7  | Mem 5    | 3  | Sp 3    | Medium
Story    | BTB-57 | Error pages (404, 500)                     | BTB-7  | Mem 5    | 1  | Sp 3    | Low
Story    | BTB-58 | Navbar + footer                            | BTB-7  | Mem 5    | 3  | Sp 1    | Highest
Story    | BTB-59 | Dockerfiles                                | BTB-8  | Mem 1    | 3  | Sp 3    | Highest
Story    | BTB-60 | GitHub Actions CI                          | BTB-8  | Mem 1    | 5  | Sp 3    | Highest
Story    | BTB-61 | Cloud deployment                           | BTB-8  | Mem 1    | 5  | Sp 3    | Highest
Story    | BTB-62 | README                                     | BTB-8  | Mem 1    | 2  | Sp 3    | Medium
         |        |                                            |        |          |    |         |
Task     | BTB-63 | Agency entity + repository                 | BTB-3  | Mem 2    | 2  | Sp 1    | High
Task     | BTB-64 | Booking entity + repository                | BTB-5  | Mem 3    | 2  | Sp 1    | High
Task     | BTB-65 | BookingService full logic                  | BTB-5  | Mem 3    | 3  | Sp 2    | Highest
Task     | BTB-66 | BookingController REST API                 | BTB-5  | Mem 3    | 2  | Sp 2    | Highest
Task     | BTB-67 | Unit tests: BookingService                 | BTB-5  | Mem 3    | 2  | Sp 3    | High
Task     | BTB-68 | Seat selection Thymeleaf page              | BTB-7  | Mem 5    | 3  | Sp 2    | High
Task     | BTB-69 | Payment entity + repository                | BTB-6  | Mem 4    | 2  | Sp 1    | High
Task     | BTB-70 | PaymentRepository queries                  | BTB-6  | Mem 4    | 1  | Sp 1    | High
Task     | BTB-71 | PaymentService logic                       | BTB-6  | Mem 4    | 3  | Sp 1    | High
Task     | BTB-72 | PaymentController REST API                 | BTB-6  | Mem 4    | 2  | Sp 1    | High
Task     | BTB-73 | Unit tests: PaymentService                 | BTB-6  | Mem 4    | 2  | Sp 3    | High
Task     | BTB-74 | Payment checkout Thymeleaf page            | BTB-7  | Mem 5    | 3  | Sp 2    | High
Task     | BTB-75 | End-to-end testing                         | BTB-8  | ALL      | 5  | Sp 3    | Highest
Task     | BTB-76 | Bug fixes from testing                     | BTB-8  | ALL      | 5  | Sp 3    | Highest
Task     | BTB-77 | SonarQube cleanup                          | BTB-8  | ALL      | 3  | Sp 3    | High
Task     | BTB-78 | Demo preparation                           | BTB-8  | ALL      | 2  | Sp 3    | Highest
         |        |                                            |        |          |    |         |
Bug      | BTB-79 | (Reserved for bugs found during Sprint 2)  | -      | -        | -  | Sp 2/3  | -
Bug      | BTB-80 | (Reserved for bugs found during Sprint 3)  | -      | -        | -  | Sp 3    | -
```

### Story Points Summary Per Sprint

```
Sprint 1 (Foundation):
  Member 1: 16 pts  (project setup + auth)
  Member 2: 14 pts  (entity + CRUD APIs)
  Member 3: 12 pts  (trip entity + search)
  Member 4:  9 pts  (payment entity + API)
  Member 5: 14 pts  (home + auth pages)
  TOTAL:    65 pts

Sprint 2 (Core Features):
  Member 1: 13 pts  (RBAC + Docker + profile)
  Member 2: 15 pts  (remaining CRUD)
  Member 3: 16 pts  (booking flow)
  Member 4: 15 pts  (payment + refund)
  Member 5: 21 pts  (search + seat + payment pages)
  TOTAL:    80 pts

Sprint 3 (Integration & Deploy):
  Member 1: 18 pts  (deploy + CI/CD + SonarQube)
  Member 2:  2 pts  (tests + bug fixes)
  Member 3: 16 pts  (my bookings + cancel + admin)
  Member 4:  5 pts  (admin payments + tests)
  Member 5: 12 pts  (admin dashboard + profile + errors)
  ALL:      15 pts  (testing + bugs + demo)
  TOTAL:    68 pts
```

---

## 10. Workflow Customization

### Step 10.1: Customize the Workflow

1. Go to **Project Settings** -> **Board** -> **Workflows** (or **Columns**)
2. Set up this workflow:

```
+----------+     +---------+     +-------------+     +---------+     +------+
| BACKLOG  | --> | TO DO   | --> | IN PROGRESS | --> | CODE    | --> | DONE |
|          |     |         |     |             |     | REVIEW  |     |      |
+----------+     +---------+     +-------------+     +---------+     +------+
                                       |                   |
                                       |    +---------+    |
                                       +--> | TESTING | ---+
                                            +---------+

  Transitions:
    BACKLOG     -> TO DO         (Sprint Planning: ticket moved to sprint)
    TO DO       -> IN PROGRESS   (Member starts working on it)
    IN PROGRESS -> CODE REVIEW   (PR created on GitHub)
    CODE REVIEW -> TESTING       (PR approved, testing needed)
    CODE REVIEW -> IN PROGRESS   (PR has requested changes, back to dev)
    TESTING     -> DONE          (Testing passed, merged)
    TESTING     -> IN PROGRESS   (Bug found during testing)
    Any status  -> BACKLOG       (De-prioritized, moved back)
```

### Step 10.2: Set Up Workflow in JIRA

For **Team-managed projects:**
1. Go to Board
2. Click column header -> Edit
3. Rename columns to match above
4. Drag and drop to reorder

For **Company-managed projects:**
1. Go to **Project Settings** -> **Workflows**
2. Click **Edit** on the active workflow
3. Add statuses: Backlog, To Do, In Progress, Code Review, Testing, Done
4. Add transitions between them (arrows)
5. Publish the workflow

---

## 11. Labels, Components & Filters

### Step 11.1: Create Labels

Labels help you categorize and filter tickets. Create these:

```
backend          - Any server-side Java code
frontend         - Thymeleaf templates, CSS, JS
database         - DB schema changes, queries
api              - REST API endpoints
security         - Auth, JWT, Spring Security
testing          - Unit tests, integration tests
devops           - Docker, CI/CD, deployment
bug              - Bug fixes
documentation    - README, comments, docs
urgent           - Needs immediate attention
blocked          - Blocked by another ticket or external dependency
```

To create labels: Just type them when creating a ticket. JIRA auto-creates new labels.

### Step 11.2: Create Components

Components represent the modules/packages of your project:

1. Go to **Project Settings** -> **Components**
2. Create:

```
Component Name       | Lead      | Description
---------------------+-----------+-------------------------------------------
user-auth            | Member 1  | Authentication, registration, security
agency-service       | Member 2  | Agency, bus, driver, route management
booking-service      | Member 3  | Trips, bookings, seat management
payment-service      | Member 4  | Payments, refunds, payment history
frontend-thymeleaf   | Member 5  | All Thymeleaf pages, CSS, JS
infrastructure       | Member 1  | Docker, CI/CD, cloud deployment
shared-models        | Member 1  | Address entity, shared DTOs
```

When creating a ticket, set its Component. This lets you filter: "Show me all booking-service tickets."

### Step 11.3: Create Saved Filters

Go to **Filters** -> **Advanced issue search** (JQL):

**My Open Tickets:**
```jql
project = BTB AND assignee = currentUser() AND status != Done ORDER BY priority DESC
```

**All In Progress:**
```jql
project = BTB AND status = "In Progress" ORDER BY assignee
```

**Sprint 1 Tickets:**
```jql
project = BTB AND sprint = "Sprint 1 - Foundation" ORDER BY priority DESC
```

**Member 2's Tickets:**
```jql
project = BTB AND assignee = "member2_username" ORDER BY status, priority DESC
```

**Bugs Only:**
```jql
project = BTB AND type = Bug ORDER BY priority DESC, created DESC
```

**Blocked Tickets:**
```jql
project = BTB AND labels = blocked ORDER BY priority DESC
```

**Overdue Tickets (past sprint end but not done):**
```jql
project = BTB AND status != Done AND sprint in closedSprints() ORDER BY priority DESC
```

**All Backend Tickets:**
```jql
project = BTB AND component = "booking-service" AND status != Done
```

Save each filter with a descriptive name. These appear in your left sidebar.

---

## 12. How Each Member Uses JIRA Daily

### Daily Standup (15 minutes - every morning)

Each member answers 3 questions:

```
1. What did I do yesterday?     -> Show DONE tickets
2. What will I do today?        -> Show IN PROGRESS tickets  
3. Any blockers?                -> Show BLOCKED tickets
```

### Member 2's Typical Day (Example)

**Morning (9:00 AM):**

1. Open JIRA: https://busbooking.atlassian.net
2. Click **Board** -> See Sprint 1 board
3. Find your ticket in "TO DO" column: `BTB-23: Add new bus`
4. **Click the ticket** -> Click **Status dropdown** -> Change to **In Progress**
5. You can also drag the ticket card from "TO DO" to "IN PROGRESS" on the board

**During Work (9:00 - 5:00):**

6. Open the ticket, read the description and acceptance criteria
7. Write the code in IntelliJ (on branch `feature/agency-bus-service`)
8. **Add comments** on the ticket as you work:
   ```
   "Created Bus entity and BusRepository. Starting BusService now."
   ```
9. If you're blocked, **add a comment**:
   ```
   "Blocked: Need Member 3 to finish Trip entity first since Bus references it."
   ```
   Add the `blocked` label to the ticket.

**End of Day (5:00 PM):**

10. Push code to GitHub: `git push origin feature/agency-bus-service`
11. If feature is complete, create a **Pull Request** on GitHub
12. Move ticket to **Code Review** status
13. Add a comment with the PR link:
    ```
    "PR created: https://github.com/sarthakpawar0912/bus-ticket-booking-system/pull/5"
    ```

**When PR is approved:**

14. Admin merges the PR
15. Move ticket to **Done**
16. Pick next ticket from "TO DO"

### Logging Work Time (Optional but Impressive)

1. Open a ticket
2. Click **Log work** (or the clock icon)
3. Enter: `2h 30m`
4. Add description: "Implemented BusService CRUD methods"
5. This shows up in reports and time tracking

---

## 13. GitHub + JIRA Integration

### Option A: Smart Commits (Free - No Plugin Needed)

Use JIRA ticket IDs in your git commit messages:

```bash
# Format: TICKET-ID #action parameter

# Move ticket to "In Progress"
git commit -m "BTB-23 #in-progress Create Bus entity with JPA mappings"

# Move ticket to "Done" and log time
git commit -m "BTB-23 #done #time 2h Add BusController REST endpoints"

# Just reference the ticket (adds comment on JIRA)
git commit -m "BTB-23 Add validation for registration number uniqueness"

# Add a comment to the ticket
git commit -m "BTB-23 #comment Fixed duplicate bus number check"
```

**How to enable Smart Commits:**

1. Go to **https://busbooking.atlassian.net**
2. Click **Apps** -> **Find new apps** -> Search "GitHub for JIRA"
3. Install **GitHub for Jira** (free by Atlassian)
4. Connect your GitHub account and select the repository

### Option B: Atlassian GitHub App (Recommended)

1. Go to **github.com/marketplace/jira-software-github**
2. Install the **Jira Software + GitHub** integration
3. Authorize for your org/account
4. Select `bus-ticket-booking-system` repository
5. Back in JIRA, go to **Project Settings** -> **Toolchain** -> **GitHub** -> Connect

**What this gives you:**

- JIRA tickets show linked GitHub branches, commits, and PRs
- GitHub PRs show linked JIRA tickets
- Ticket status can auto-update based on PR status

### Option C: Branch Naming Convention

Name your Git branches with the JIRA ticket ID:

```bash
# When starting work on BTB-23
git checkout -b BTB-23-add-new-bus

# JIRA will automatically link this branch to ticket BTB-23
```

Same for PR titles:
```
BTB-23: Add new bus with registration validation
```

JIRA automatically picks up the `BTB-23` prefix and links the PR to the ticket.

### What the Integration Looks Like

**On JIRA ticket BTB-23:**
```
Development Panel:
  Branch:  BTB-23-add-new-bus (feature/agency-bus-service)
  Commits: 3 commits
    - "BTB-23 Create Bus entity with JPA mappings" (2h ago)
    - "BTB-23 Add BusService CRUD methods" (1h ago)
    - "BTB-23 Add BusController endpoints" (30m ago)
  Pull Request: #5 "BTB-23: Add new bus" (OPEN -> MERGED)
```

**On GitHub PR #5:**
```
Linked JIRA Issues:
  BTB-23: Add new bus (IN PROGRESS -> DONE)
```

---

## 14. JIRA Dashboard & Reports

### Step 14.1: Create a Custom Dashboard

1. Click **Dashboards** (top menu) -> **Create dashboard**
2. Name: `Bus Booking - Team Dashboard`
3. Layout: 2 columns

**Add these Gadgets (click "Add gadget"):**

Left Column:
```
1. Sprint Burndown Chart
   - Shows remaining work vs time
   - Should trend downward toward 0

2. Sprint Health Gadget
   - Shows completed vs remaining story points

3. Activity Stream
   - Shows recent updates from all team members
```

Right Column:
```
4. Pie Chart - Issues by Assignee
   - Filter: project = BTB AND sprint in openSprints()
   - Statistic: Assignee

5. Two-Dimensional Filter Statistics
   - Rows: Assignee
   - Columns: Status
   - Shows which member has how many tickets in each status

6. Filter Results - My Open Issues
   - Filter: project = BTB AND assignee = currentUser() AND status != Done
```

### Step 14.2: Sprint Reports (Available After Sprint Ends)

After completing Sprint 1, go to:

**Reports** (left sidebar) -> Select report type:

```
1. Burndown Chart
   Shows: Story points completed per day vs ideal line
   Goal:  Actual line should follow or be below the ideal line
   Problem: If actual is above ideal, team is behind schedule

2. Velocity Chart
   Shows: Story points completed per sprint
   Goal:  Increasing or stable velocity across sprints
   Use:   Predict how much work can be done in future sprints

3. Sprint Report
   Shows: Completed vs not completed vs added during sprint
   Goal:  Most tickets completed, few added mid-sprint
   Problem: Many incomplete tickets = scope was too large

4. Cumulative Flow Diagram
   Shows: Ticket count per status over time
   Goal:  "Done" area growing, "In Progress" stable (not growing)
   Problem: If "In Progress" keeps growing = bottleneck

5. Control Chart
   Shows: How long tickets take from start to done
   Goal:  Consistent cycle time (e.g., 1-2 days per ticket)
   Problem: Spikes mean some tickets took too long
```

### Step 14.3: Create a Sprint Review Report

At the end of each sprint, create a Confluence page (or Google Doc) with:

```
Sprint 1 Review - Bus Ticket Booking
Date: April 13, 2026

Planned: 65 story points
Completed: 58 story points
Carry-over: 7 story points (BTB-32 partial, BTB-44)

Demo Items:
  - User registration and login working
  - Agency, Bus, Route CRUD APIs
  - Trip creation API
  - Payment entity and basic API
  - Home page with search form
  - Login/Register pages

Blockers Encountered:
  - MySQL port conflict on Member 3's machine (resolved Day 2)
  - pom.xml merge conflict (resolved Day 3)

Retrospective:
  What went well: Clean branch strategy, no major conflicts
  What to improve: Start testing earlier, better commit messages
  Action items: Write tests alongside features in Sprint 2
```

---

## 15. Best Practices for Your Team

### Ticket Discipline

```
DO:
  - Update ticket status every time you switch tasks
  - Add comments when you make progress or hit blockers
  - Link PRs to tickets (use BTB-XX in branch/commit names)
  - Break large stories into tasks (nothing > 5 story points)
  - Close tickets the same day you finish them

DON'T:
  - Leave tickets "In Progress" for more than 2 days
  - Work on tickets not in the current sprint
  - Create tickets without descriptions or acceptance criteria
  - Have more than 2 tickets "In Progress" at the same time
  - Forget to log blockers
```

### Ticket Naming Convention

```
GOOD ticket titles:
  "Create Agency entity with JPA mappings"
  "Add bus search API with filters"
  "Fix NullPointer in BookingService.cancelBooking"
  "Create seat selection Thymeleaf page"

BAD ticket titles:
  "Do agency stuff"
  "Fix bug"
  "Frontend work"
  "Backend"
```

### Definition of Done (DoD)

A ticket is DONE when ALL of these are true:

```
[ ] Code is written and compiles without errors
[ ] Code follows the package structure (agency/, booking/, etc.)
[ ] No hardcoded credentials or secrets
[ ] Unit tests written (for service layer at minimum)
[ ] PR created with BTB-XX in the title
[ ] PR reviewed and approved by at least 1 team member
[ ] PR merged to develop branch
[ ] SonarQube shows no new bugs or vulnerabilities
[ ] Ticket moved to DONE in JIRA
[ ] Demo-able: the feature works when you show it
```

### Daily Standup Template (WhatsApp/Slack)

```
DAILY STANDUP - April 10, 2026

MEMBER 1 (Sarthak - Admin):
  Yesterday: Completed BTB-9 (project init), BTB-10 (git setup)
  Today: Working on BTB-14 (registration) and BTB-15 (login)
  Blockers: None

MEMBER 2 (Name - Agency):
  Yesterday: Completed BTB-63 (Agency entity)
  Today: Working on BTB-19 (view agencies), BTB-20 (add agency)
  Blockers: Waiting for DB seed data (BTB-11)

MEMBER 3 (Name - Booking):
  Yesterday: Started BTB-29 (trip entity)
  Today: Continue BTB-29, start BTB-64 (booking entity)
  Blockers: None

MEMBER 4 (Name - Payment):
  Yesterday: Completed BTB-69 (payment entity)
  Today: Working on BTB-71 (payment service logic)
  Blockers: None

MEMBER 5 (Name - Frontend):
  Yesterday: Completed BTB-58 (navbar + footer)
  Today: Working on BTB-47 (home page)
  Blockers: Need Member 2 to finish search API for form action
```

---

## Quick Setup Checklist for Admin

```
[ ] 1. Create Atlassian account at atlassian.com/software/jira/free
[ ] 2. Create project "Bus Ticket Booking" (key: BTB, type: Scrum)
[ ] 3. Invite 4 team members via email
[ ] 4. Set up board columns: Backlog, To Do, In Progress, Code Review, Testing, Done
[ ] 5. Create 8 Epics (BTB-1 through BTB-8)
[ ] 6. Create all Stories and Tasks (BTB-9 through BTB-78)
[ ] 7. Create Sprint 1, Sprint 2, Sprint 3 with dates
[ ] 8. Drag Sprint 1 tickets into Sprint 1
[ ] 9. Start Sprint 1
[ ] 10. Install GitHub for Jira app
[ ] 11. Create team dashboard with gadgets
[ ] 12. Share JIRA URL and credentials with team
```

### Share This With Your Team

```
============================================
  JIRA ACCESS - BUS TICKET BOOKING
============================================

URL:        https://busbooking.atlassian.net
Project:    BTB (Bus Ticket Booking)
Board:      Scrum Board

Your Account:
  (Each member uses their invited email to login)

Sprint Schedule:
  Sprint 1: Apr 9-13  (Foundation)
  Sprint 2: Apr 14-18 (Core Features)
  Sprint 3: Apr 19-23 (Integration & Deploy)

Daily Rules:
  1. Update ticket status when you start/finish work
  2. Max 2 tickets In Progress at a time
  3. Use BTB-XX in git branch names and commits
  4. Comment on tickets when blocked
  5. Attend daily standup (15 min)

Git Branch Naming:
  BTB-23-add-new-bus
  BTB-35-booking-flow
  BTB-41-payment-processing
============================================
```
