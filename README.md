KSLB SIWES Portal

SIWES Roadmap, Skills Verification & Digital Logbook Management System

A digital platform designed to manage, monitor and evaluate students undertaking the Students Industrial Work Experience Scheme (SIWES) at the Kano State Library Board (KSLB).

The platform connects students, KSLB departments, workplace supervisors and educational institutions through structured training roadmaps, competency assessments, practical verification and digital logbook management.

---

Project Overview

The KSLB SIWES Portal is designed to improve the administration, supervision, documentation and evaluation of students undertaking industrial training at the Kano State Library Board.

It provides a structured system through which students can follow department-specific training roadmaps, access curated external learning resources, demonstrate acquired knowledge, submit practical evidence and maintain digital logbooks.

The system also enables KSLB supervisors and educational institutions to monitor student progress remotely.

This project is not a Learning Management System (LMS). It does not host lessons, course videos, textbooks or educational materials. Instead, it manages SIWES training activities, learning objectives, external resource references, competency verification and student performance records.

Core Objectives

- Digitise SIWES application, placement and administrative workflows.
- Provide structured training roadmaps for different KSLB departments.
- Track student progress against defined learning objectives and competencies.
- Integrate AI-assisted knowledge assessments and evaluation.
- Verify practical competencies through supervisor-confirmed evidence.
- Generate draft digital logbook entries from documented student activities.
- Enable remote monitoring by institutional coordinators and school supervisors.
- Provide reliable reporting, attendance records and performance analytics.
- Maintain accountability through role-based access controls and audit trails.

Key Features

1. Student Registration and Application

Students will be able to:

- Create accounts and maintain their profiles.
- Submit academic and institutional information.
- Upload SIWES introduction letters and required documents.
- Track application and placement status.
- View assigned departments, supervisors and training schedules.

2. Administrative Management

Authorised KSLB administrators will be able to:

- Review and approve student applications.
- Create and manage departments.
- Assign students to departments and supervisors.
- Configure placement periods and training schedules.
- Manage institutions and supervisor accounts.
- Create, edit and publish training roadmaps.
- Monitor student progress and generate reports.

Initial departments:

- ICT Department
- Library Services

Additional departments will be configurable.

3. SIWES Training Roadmaps

Each student will receive a structured roadmap based on their assigned department, placement duration and approved roadmap version.

Roadmaps will contain:

- Training phases and milestones.
- Learning objectives.
- Required competencies.
- Practical activities.
- Assessment requirements.
- Curated external learning resources.
- Completion criteria.

Placement durations and schedules will be configurable rather than restricted to fixed periods.

4. External Learning Resources

The portal will provide curated links to reputable external learning platforms, technical documentation, tutorials and reference materials.

It will store resource metadata and URLs rather than hosting the actual learning content.

5. AI-Assisted Assessment Engine

The assessment engine will generate questions based on:

- The student's assigned roadmap.
- Current training phase.
- Required skills and competencies.
- Defined learning objectives.
- Assessment difficulty.
- Approved assessment rubrics.

The system will evaluate submitted answers and provide:

- Assessment scores.
- Feedback and explanations.
- Demonstrated knowledge.
- Identified knowledge gaps.
- Recommendations for improvement.

AI-generated evaluations will be traceable and subject to configurable assessment rules.

6. Practical Skills Verification

Practical competency must be verified independently from theoretical knowledge.

Students may submit practical evidence and activity records. Assigned KSLB supervisors will review and confirm practical activities before they are marked as verified.

AI assessments alone cannot establish that a student physically performed a practical task.

7. Digital Logbook Management

The system will support structured digital logbook management.

Its workflow will be:

1. Student records actual activities.
2. AI assists in preparing a draft entry using documented information.
3. Student reviews and confirms or edits the draft.
4. KSLB supervisor reviews and endorses the entry.
5. School supervisor can monitor the approved record.

Original submissions, edits, approvals and review history will be retained.

AI must never invent activities, tools, achievements or supervisor approvals.

Institutional acceptance of digital logbooks will be confirmed before replacing any required official paper logbook.

8. Supervisor and Institution Portals

The platform will support:

- KSLB supervisors.
- Individual school supervisors.
- Institutional SIWES coordinators.

Institution coordinators will only access students belonging to their institution. Individual school supervisors will access students specifically assigned to them.

9. Attendance and Reporting

The system will maintain separate records for:

- Attendance and punctuality.
- Training progress.
- Assessment performance.
- Practical competency.
- Logbook completion.
- Supervisor reviews.
- Placement completion.

Reports will support student, department, institution and administrative monitoring.

User Roles

Role| Responsibilities
Student| Applications, training, assessments, evidence and logbooks
KSLB Administrator| Applications, placements, departments, users and system administration
KSLB Supervisor| Student supervision, practical verification and logbook approval
Department Coordinator| Department-level training and roadmap management
School Supervisor| Monitoring assigned students
Institution Coordinator| Monitoring students from their institution

Permissions will be enforced on the server, with institution, department and assignment-based access restrictions.

Technology Stack

The intended architecture is a TypeScript modular monolith.

Component| Technology
Frontend| React
Language| TypeScript
Build tooling| Vite
Backend| Hono
Application hosting| Cloudflare Workers
Database| PostgreSQL
Database provider| Neon
ORM| Drizzle ORM
Database connectivity| Cloudflare Hyperdrive
Document storage| Cloudflare R2
Source control| GitHub
Development environment| GitHub Codespaces
Domain and DNS| Cloudflare DNS

The hosting architecture is designed to be portable so that the application can migrate to a conventional server if its operational requirements grow.

Architecture

                    STUDENTS / STAFF
                           |
                           v
                  CUSTOM DOMAIN
                           |
                           v
                   CLOUDFLARE DNS
                           |
                           v
                 CLOUDFLARE WORKER
                   /             \
                  /               \
                 v                 v
          REACT FRONTEND       HONO API
                                    |
                    +---------------+---------------+
                    |               |               |
                    v               v               v
                NEON DB        CLOUDFLARE R2    AI PROVIDER
              PostgreSQL      Private Files    Assessments
                    |
                    v
             AUDIT / REPORTING

Security and Data Protection

Security is a core architectural requirement.

The system will implement:

- Secure authentication and session management.
- Role-based access control.
- Institution and department data isolation.
- MFA for privileged accounts.
- Private document storage.
- Secure document upload validation.
- Encryption in transit and appropriate encryption at rest.
- Audit logging for sensitive operations.
- Session revocation and account recovery.
- Database backup and recovery procedures.
- Data retention and privacy policies.
- Protection of AI and database credentials.

The project will be developed with Nigeria's applicable data protection requirements in mind, including the Nigeria Data Protection Act 2023.

Development Principles

1. Build a modular monolith before considering microservices.
2. Enforce permissions on the backend.
3. Preserve data integrity and audit history.
4. Use versioned roadmaps and assessment configurations.
5. Keep AI-assisted records traceable to actual evidence.
6. Separate theoretical assessments from practical verification.
7. Keep external learning resources as references, not hosted lessons.
8. Write and run tests before deploying changes.
9. Use migrations for database schema changes.
10. Never perform destructive database resets without explicit approval.

Project Structure

The intended project structure is:

kslb-siwes-portal/
├── apps/
│   ├── web/                  # React frontend
│   └── api/                  # Hono backend
├── packages/
│   ├── database/             # Schema and migrations
│   ├── shared/               # Shared types and validation
│   └── config/               # Shared configuration
├── docs/
│   ├── PROJECT_OVERVIEW.md
│   ├── SOFTWARE_REQUIREMENTS.md
│   ├── DATABASE_DESIGN.md
│   ├── RBAC_MATRIX.md
│   ├── CURRICULUM_SPECIFICATION.md
│   ├── API_SPECIFICATION.md
│   ├── SECURITY_REQUIREMENTS.md
│   └── DEVELOPMENT_ROADMAP.md
├── tests/
├── .env.example
├── .gitignore
├── README.md
└── package.json

The actual structure may be adjusted to match the selected Cloudflare application template.

Development Setup

Prerequisites

- Node.js (supported LTS version)
- npm
- Git
- GitHub account
- Cloudflare account
- Neon PostgreSQL account

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY

Install dependencies:

npm install

Configure environment variables using the provided ".env.example".

Start the development server:

npm run dev

Run tests:

npm test

Build the application:

npm run build

Deployment will use the project's configured Cloudflare Wrangler workflow.

Deployment Strategy

The initial deployment target is:

- Cloudflare Workers for the frontend and API.
- Neon for PostgreSQL.
- Cloudflare R2 for private document storage.
- Cloudflare DNS for the custom domain.
- GitHub for source control and automated deployment.

The application will initially target a controlled pilot deployment. Free-tier services will be used where practical, with usage limits, backups, security and availability monitored carefully.

Development Roadmap

Phase| Scope
1| Infrastructure and project foundation
2| Authentication, users and permissions
3| Student applications and placements
4| Departments and training roadmaps
5| External resources and assessments
6| Practical evidence and competency verification
7| Digital logbooks and supervisor approvals
8| Institution portals and reporting
9| Security testing and production deployment

Project Status

Status: Planning and foundation stage

The project is being prepared for implementation. Features described in this README represent the intended product scope and should not be interpreted as already deployed or completed.

Contribution and Governance

Development should follow the project's engineering documentation and architectural decisions.

Changes affecting student records, permissions, assessments, placement workflows or audit history must be reviewed and tested before deployment.

Licence

A project licence will be selected and documented before public distribution.

---

Kano State Library Board (KSLB)
SIWES Roadmap, Skills Verification & Digital Logbook Management System

Structured industrial training. Verified competencies. Accountable supervision.
