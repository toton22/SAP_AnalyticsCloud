# SAP UCC workshop — Introduction to SAP Cloud Solutions: SAP Analytics Cloud

**When:** Friday 2 October 2026, 09:00–16:30 CEST (12:30–20:00 IST), online (GoTo)
**Who:** Andreas Hofstetter and Anke Thurau, SAP UCC Magdeburg
**Format:** whiteboard protocol built live in PowerPoint + overview slide deck + SAP UA curriculum 3.0 hand-out

## Agenda

1. Components of the SAP Analytics Cloud
2. Authorisation management in SAC
3. User groups of the tools
4. SAP UA SAC Curriculum — modules and variants of usage

## 1. The whiteboard: where SAC sits in a BI architecture

Built bottom-up on one slide. Read it as a stack:

| Layer | What lives there | Who owns it |
|---|---|---|
| Information access & broadcasting | Broadcasting, reporting portal, self service | Power users / data analysts |
| Visualization / presentation | Excel integration (Analysis), web reporting (Story), dashboarding (Story) | Power users |
| **Data model (Modeler)** | the seam between SAC and the warehouse | both |
| Query layer | choose the analytic dimensions, filter them → a "part cube" (e.g. Time × Employee × Customer) → selections, calculations | warehouse / reporting solution |
| Reporting layer — architected data mart | free pivotable analytic view, denormalised: all dimensions are key fields; authorisation on data level | warehouse |
| Integration layer — EDW transformation / corporate memory | combine data, pre-aggregate to higher levels, reporting logic (no business logic) | warehouse |
| Staging layer — open operational data store | detailed data as the basis for integration; source-system-specific, field-based structure | warehouse |
| Data sources — OLTP systems | CRM (C4C), ERP, databases → replicated upwards | source owners |

Left brackets: "DataWarehouse (SAP BW / SAP Datasphere)" spans staging → query; "BI front-end tools" spans visualization → broadcasting. Right arrows: *replication* (sources → staging), *reporting-solution based* (staging → query), *responsibility of power users (data analyst)* (modeler → broadcasting).

## 2. Components of SAC (slide 3)

- Self-service / distribution: Portal · Smartphone/Tablet · Distribution (scheduling)
- Tools: Story Builder (stories) · Analysis SAC edition (Excel workbooks / PowerPoint). Digital Boardroom and Analytics Designer were crossed out live by the trainer.
- Functionalities / backend: Data model (Modeler) · Planning (functions, simulation, workflow) · Predictive (Smart Insights, Smart Discovery, predictive forecasting, Smart Predict) · Monitoring · Identity management · Connection to source systems

## 3. Import vs live (slide 4)

**Import connection** — CSV files; stored in the SAC repository; replication on demand or scheduled; encrypted storage.
⚠ 250 MB storage per SAC user; more only by buying additional user licences.

**Live connection** — to SAP BW / S/4HANA / HANA; the transfer object is the **SAP BEx query**; the queried data area is buffered in SAC while the application is open and deleted when it closes; logon with BW credentials or SSO; encrypted transmission.
⚠ Authentication with the UCC username; the e-mail address in Identity Management must be maintained by students at first login.

## 4. SAC Modeler (slide 5)

Data source and starting point for every SAC tool. You model: analysis dimensions with attributes and hierarchies; basic key figures with currency or quantity units; basic calculated key figures. Two model types: **account-based (standard)** and **key-figure (measure-based)**.

Restrictions worth memorising:
- no geo functionality in the key-figure model; some automatic-forecast widgets are restricted by connection type
- no direct use of BEx queries with a live connection in the tools — one model per BEx query, mandatory
- descriptions of restricted/calculated key figures with line breaks must be maintained manually in the SAC model
- with import, do the heavy transformations in the ETL process *before* the file reaches SAC (performance)

## 5. Account-based vs key-figure-based (slide 6)

Account-based: key figures are characteristics of the account dimension; only two key figures (amount, quantity); adapts well to a volatile KPI portfolio; avoids sparse matrices (better performance).
Key-figure-based: each key figure is its own field with its own unit; obsolete key figures must stay for consistency; risk of sparse matrices (poorer performance).

## 6. Story Builder vs Analytics Designer vs Planning (slides 7, 8, 10)

- **Story Builder** — uses existing models; web reports and small dashboards; responsive design for power users; widgets (charts, tables, text, pictures, geo maps); analysis: data view in widget, global/widget filters, restricted and calculated key figures, sorting, rankings, thresholds, linked analysis. Created and maintained by power users. Curriculum: Story Builder exercise + case study.
- **Analytics Designer** — complex web applications and dashboards; themes + CSS; extra widgets (buttons, drop-downs, input fields, radio buttons); scripting with global/local variables, URL start parameters, JavaScript-like syntax. Created and maintained by IT professionals. Curriculum: Analytics Designer case study.
- **SAC Planning** — on SAC models and SAP BW BPC models; data entry stored in the model, plan versions, simulations, predictive planning (rolling forecast + simulation), integrated planning workflow, Excel integration. Separate SAP UA curriculum.

## 7. Authorisation (slides 13, 15)

Five elements: **User (identity)** → member of **Team**; **Folder shares** → user or team; **Roles** → user or team; **Functionalities** → bundled into roles.

**Workspace**: a container with its own folder structure outside the regular SAC folders; access rights only at team level (no individual users); administered by workspace administrators, who need not be members of the authorised teams. Benefits: project level becomes part of the authorisation system; workspace users see only the workspace, not the general folder structure; folder sharing only within the workspace's teams/users and only with the "Share" permission.

## 8. SAP UA SAC curriculum 3.0 (slides 19, 20)

Framework: lecturer notes, overview presentation, and the mandatory **Navigation in SAC** exercise. Modules: SAC Modeler (case study), SAC Stories (exercise), SAC Stories (case study), SAC Story Builder Advanced (case study: sales dashboard as web app, information design, responsive design, themes/CSS, JavaScript).

Four delivery variants:
1. Introduction / overview — business & technology students — overview presentation + Story exercise *presented by the lecturer*
2. SAC Story, accompanied exercise — same audience — overview + Story exercise *hands-on by students*
3. SAC Story, case study — same audience — overview + exercise + Story case study + optional Modeler case study
4. SAC Analytics Designer, case study — information-science students — everything above + Story Builder Advanced + Modeler

## Hand-out (ucc-curriculum-3.0/)

- 02 Navigation in SAC (case study, beginner, 22 pp.) — log on, profile, build the UI, folders, share, log out, tips
- 03 Story Builder exercise (60 min, 17 pp.) — Alex Kuhn's three change requests on the existing sales dashboard
- 04a Story Builder case study I (220 min, 83 pp., 20 steps) — build the Global Bike sales dashboard
- 04b Modeler case study II (130 min, 36 pp., 8 steps + challenge) — build the Global Bike analytic model from Excel, load 2019, story, "Discount %" in model vs story

Tenant: ucc-pilot-sac.eu10.hcs.cloud.sap (UCC-issued user; Google Chrome recommended).
