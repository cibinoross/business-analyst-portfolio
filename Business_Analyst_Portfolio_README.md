# Business Analyst Portfolio

### SaaS Product Analysis · Requirements Engineering · UAT · AI/ML Workflows


**Target roles:** Business Analyst · Product Analyst · Product
Operations Analyst\
**Core tools:** Jira · Confluence · Excel · Google Sheets · ChatGPT ·
Claude · Lovable · chatPRD\
**Domain experience:** SaaS · Media Intelligence · Search & Monitoring ·
Newsletter Workflows · Alerting · AI-Assisted Systematic Literature
Reviews

------------------------------------------------------------------------

## Contents

-   [Profile](#profile)
-   [How I approach business
    analysis](#how-i-approach-business-analysis)
-   [Skills and tools](#skills-and-tools)
-   [Case study 1 --- OneSearch and search
    workflows](#case-study-1--onesearch-and-search-workflows)
-   [Case study 2 --- Newsletter management and content
    workflows](#case-study-2--newsletter-management-and-content-workflows)
-   [Case study 3 --- MadeAI product support and
    validation](#case-study-3--madeai-product-support-and-validation)
-   [Case study 4 --- UAT, release coordination, and knowledge
    transfer](#case-study-4--uat-release-coordination-and-knowledge-transfer)
-   [Selected requirements artefacts](#selected-requirements-artefacts)
-   [Proposed mock case study --- Alert Statistics
    dashboard](#proposed-mock-case-study--alert-statistics-dashboard)
-   [Additional product-analysis
    examples](#additional-product-analysis-examples)
-   [How I measure success](#how-i-measure-success)
-   [Confidentiality and evidence
    notes](#confidentiality-and-evidence-notes)
-   [Contact](#contact)

------------------------------------------------------------------------

## Profile

I am a Business Analyst / Product Operations professional with
experience supporting SaaS products, clarifying business needs,
documenting functional requirements, and coordinating work between
stakeholders, Product, Engineering, analysts, and Machine Learning
teams.

My work at Fullintel has covered media-intelligence workflows such as
search and monitoring, article management, newsletter generation,
alerts, customer configuration, and administrative tools. My MadeAI work
has included trial setup, user and project configuration, requirements
clarification, UAT coordination, issue reporting, and validation of
AI-assisted systematic literature review workflows.

I focus on understanding the problem before proposing a solution,
documenting expected behaviour clearly, considering edge cases and
dependencies, and making requirements testable.

### What I bring

  -----------------------------------------------------------------------
  Capability                          Practical application
  ----------------------------------- -----------------------------------
  Requirements engineering            Clarifying needs, documenting
                                      functional requirements, writing
                                      Jira tickets and acceptance
                                      criteria

  Workflow analysis                   Understanding existing behaviour,
                                      identifying gaps, defining expected
                                      states and user journeys

  Stakeholder coordination            Connecting customer feedback with
                                      Product, Engineering, ML, and
                                      operational teams

  UAT and issue analysis              Preparing scenarios, recording
                                      reproduction steps, documenting
                                      expected versus actual behaviour,
                                      coordinating retesting

  Product operations                  Trial configuration, release
                                      coordination, product
                                      documentation, handover and process
                                      improvement

  AI/ML product support               Workflow validation,
                                      reference-based comparison, issue
                                      tracking and feedback coordination
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## How I approach business analysis

``` text
Business need
     |
     v
Understand current behaviour (AS-IS)
     |
     v
Identify gaps, users, rules and dependencies
     |
     v
Define target behaviour (TO-BE)
     |
     v
Write requirements + user stories + acceptance criteria
     |
     v
Align with stakeholders and technical teams
     |
     v
Validate through UAT and defect follow-up
     |
     v
Document outcomes and improvement opportunities
```

For each requirement, I aim to make clear:

1.  **Who** needs the change and **why**.
2.  What happens today and what should happen instead.
3.  The functional rules, field behaviour, state changes, and
    dependencies.
4.  What should happen for empty, invalid, duplicate, or boundary cases.
5.  How a tester can verify the result objectively.

------------------------------------------------------------------------

## Skills and tools

### Business analysis

-   Requirements clarification and functional specification
-   Functional Requirements Documents (FRDs)
-   User stories and acceptance criteria
-   Workflow and gap analysis
-   Business rules and edge-case definition
-   Stakeholder communication and cross-functional coordination
-   Product documentation and knowledge transfer

### Testing and delivery

-   User Acceptance Testing (UAT) coordination
-   Test scenarios and expected-result definition
-   Defect reporting and reproduction steps
-   Regression considerations
-   Release-ticket tracking and deployment-status documentation
-   Trial monitoring and issue follow-up

### Tools used or referenced in my work

  -----------------------------------------------------------------------
  Tool                                Portfolio-relevant use
  ----------------------------------- -----------------------------------
  Jira                                Requirements, tickets, acceptance
                                      criteria, defects and release
                                      tracking

  Confluence                          Product documentation and knowledge
                                      sharing

  Excel / Google Sheets               Structured tracking, validation
                                      records and reporting

  ChatGPT / Claude                    AI-assisted drafting, analysis
                                      support and structured
                                      documentation

  Lovable / chatPRD                   No-code and AI-assisted product
                                      ideation / requirement exploration
  -----------------------------------------------------------------------

*Tools are listed based on my described work and usage. I do not claim
SQL, Power BI, or other technical tools as hands-on experience unless I
can demonstrate that work separately.*

------------------------------------------------------------------------

# Case study 1 --- OneSearch and search workflows

**Domain:** Media intelligence SaaS\
**Focus:** Search behaviour, filters, article metadata, validation, and
user experience\
**Work type:** Requirements and product-enhancement analysis based on
issues and requirements handled in my Fullintel work

## 1. Context

Search and monitoring workflows help analysts locate relevant media
content from multiple sources. The experience depends on clear source
selection, Boolean query behaviour, date ranges, article metadata, and
filters that make large result sets easier to narrow.

My work included documenting search-related issues and enhancements,
clarifying expected UI behaviour, and translating observations into
requirements suitable for technical implementation and testing.

## 2. Example problem areas

-   Search filters need predictable selection and deselection behaviour.
-   Search validation messages should appear at the appropriate point in
    the workflow.
-   Date-range controls must reflect the actual criteria applied to
    results.
-   Article cards should display metadata consistently.
-   Source selection and source-type distinctions should be
    understandable.
-   Existing workflows must remain functional when the UI is enhanced.

## 3. Example requirement: metadata-based second-level filters

**User story**

> As an analyst, I want to refine search results using article metadata,
> so that I can narrow a large result set to the content most relevant
> to my research.

**Filters in scope**

-   Source
-   Source Country
-   Source Rank
-   Reach
-   Media Type
-   Language
-   Tonality
-   Source Type

**Functional requirements**

1.  Each filter displays values available in the result set.
2.  Each filter value displays an article count based on the
    corresponding metadata.
3.  Users can select and deselect filter values.
4.  Applied selections refine the displayed results.
5.  Multiple filter values and filter groups work together according to
    the agreed filtering logic.
6.  Counts and results remain consistent with the active query and other
    applied filters.
7.  The UI clearly distinguishes an empty result set from a
    query-validation error.

**Acceptance criteria**

-   [ ] The eight required filter groups are available.
-   [ ] Each filter value displays its corresponding article count.
-   [ ] Selecting a value updates the result set.
-   [ ] Deselecting a value removes that selection from the applied
    criteria.
-   [ ] Multiple selected filters are applied consistently.
-   [ ] When no articles match the applied criteria, a clear empty-state
    message is shown.
-   [ ] Invalid Boolean syntax produces a validation message at the
    agreed validation point, rather than unexpectedly while the user is
    still editing.
-   [ ] Existing search-source, date-range, and article-opening
    behaviours are not unintentionally broken.

## 4. Example requirement: date and time search

**Problem observed in a reported scenario**

A search using a selected station and a precise start/end time returned
clips outside the requested time window. This made the search results
inconsistent with the user's explicit criteria.

**Expected behaviour**

The system should apply the selected station, date, start time, and end
time consistently, and return only clips whose relevant time metadata
falls within the defined range. The exact timestamp field used for
comparison should be confirmed with Engineering.

**Acceptance criteria**

-   [ ] The selected station is applied to the search.
-   [ ] The selected date and start/end times are applied to the query.
-   [ ] Results outside the defined time window are excluded.
-   [ ] The UI displays the selected criteria accurately.
-   [ ] Boundary behaviour at the start and end times is documented and
    tested.
-   [ ] An empty result set is handled clearly.

## 5. Analysis method

1.  Capture the exact user action and current result.
2.  Record the selected filters or query, including dates and source.
3.  State the expected behaviour independently of the current
    implementation.
4.  Identify data or metadata dependencies that may affect the result.
5.  Document acceptance criteria and regression areas.
6.  Validate the fix with the original reproduction scenario and related
    edge cases.

## 6. Intended value

-   More precise search results.
-   Better understanding of why articles appear in a result set.
-   Less manual effort when narrowing content.
-   Clearer communication between analysts, Product, Engineering, and
    QA.

**Status note:** This case study describes search-related requirements
and issue-analysis work. Individual enhancements should be marked as
delivered only when verified against the relevant Jira ticket or
release.

------------------------------------------------------------------------

# Case study 2 --- Newsletter management and content workflows

**Domain:** Media intelligence SaaS\
**Focus:** Article selection, section ordering, summaries, template
behaviour, and report output\
**Work type:** Requirements definition, issue analysis,
customer-specific workflow support, and UAT coordination

## 1. Context

The newsletter workflow brings together article selection, content
categorisation, summaries, section order, formatting, and delivery. A
change can look correct in one view but behave differently in a test
email, individual email, distribution-list email, or downloaded HTML.

My work included documenting expected behaviour across these workflow
stages and helping technical teams understand the exact conditions under
which issues occurred.

## 2. Example requirement: selecting and removing articles

**User story**

> As an analyst, I want to select or deselect an article by clicking its
> row, so that I can manage newsletter content more efficiently without
> having to target a small checkbox.

**Functional requirements**

-   Clicking an article row toggles its selection state.
-   Clicking the checkbox continues to work.
-   The behaviour supports multiple article selections.
-   The behaviour works when adding articles to the newsletter and when
    removing articles from a newsletter section.
-   Existing drag-and-drop behaviour is retained.

**Acceptance criteria**

-   [ ] Clicking an unselected row selects its article.
-   [ ] Clicking a selected row deselects its article.
-   [ ] Checkbox interaction remains functional.
-   [ ] Multiple rows can be selected and deselected.
-   [ ] The same selection behaviour is available for adding and
    removing articles.
-   [ ] The UI accurately reflects the selected articles before the
    action is completed.
-   [ ] Existing drag-and-drop and other row actions continue to work.

## 3. Example requirement: preserving section order

**Problem observed in a reported scenario**

A section arrangement appeared correct during testing and download, but
the final report delivered through the application's Send workflow did
not consistently preserve the order. Sending through an individual-email
route behaved differently in the same scenario.

**Analysis considerations**

-   The order saved in the UI may differ from the order used during
    report generation.
-   Test, download, individual-send, and distribution-list-send paths
    may use different processing steps.
-   The setting controlling empty-section display can affect section
    arrangement.
-   Reproduction must preserve the same newsletter, section order,
    recipient configuration, and delivery method.

**Acceptance criteria**

-   [ ] The saved section order is retained when reopening the
    newsletter.
-   [ ] The same order is used for test, download, individual-send, and
    distribution-list-send outputs, where the feature is supported.
-   [ ] The behaviour is verified with the relevant empty-section
    configuration.
-   [ ] The delivered output matches the configured order.
-   [ ] Regression testing covers the affected template and other
    supported customers/templates.

## 4. Example requirement: longer manual summaries

**Business context**

A reported CKEditor limitation prevented saving a newsletter when a
manual summary exceeded the existing character limit. The requirement
raised was to increase the limit to 20,000 characters or more to
accommodate a customer workflow.

**Acceptance criteria**

-   [ ] The editor accepts the agreed maximum summary length.
-   [ ] The character counter or validation reflects the configured
    limit, if provided.
-   [ ] Saving a summary within the limit succeeds.
-   [ ] Exceeding the limit produces a clear validation message rather
    than an undefined error.
-   [ ] The saved summary is retained when reopening the newsletter.
-   [ ] Test, download, and send outputs preserve the saved content
    without truncation, subject to the supported output format.

## 5. Analysis method

``` text
User action
    |
    v
Observe UI state
    |
    v
Save / test / download / send
    |
    v
Compare output across delivery paths
    |
    v
Record mismatch and reproduction steps
    |
    v
Define expected behaviour and acceptance criteria
    |
    v
Retest the original scenario + regression cases
```

## 6. Intended value

-   More reliable newsletter creation and delivery.
-   Less repetitive article selection and correction.
-   Better consistency between the editor and final output.
-   Clearer issue reproduction and more effective UAT.

**Status note:** These examples are based on requirements and issues
described in my work. They are not a claim that every proposed
enhancement has been implemented.

------------------------------------------------------------------------

# Case study 3 --- MadeAI product support and validation

**Domain:** AI-powered systematic literature review (SLR) platform\
**Focus:** Trial configuration, requirements clarification, UAT, issue
reporting, and AI workflow validation\
**Work type:** Product administration and cross-functional coordination

## 1. Context

MadeAI supports systematic literature review workflows that involve
multiple stages and structured research outputs. These stages require
clear expectations, traceability, and a consistent method for recording
discrepancies.

My work included trial setup, user/project configuration, UAT
coordination, customer feedback capture, issue reporting, and
collaboration with Product, Engineering, and ML stakeholders.

## 2. Workflow overview

``` text
Protocol
   |
   v
Title & Abstract Screening
   |
   v
Full-Text Screening
   |
   v
Data Extraction
   |
   v
Risk of Bias
   |
   v
Evidence Synthesis
```

The exact stages and sequence depend on the configured review workflow.
The diagram represents the main validation stages used in the work
described here.

## 3. Responsibilities

-   Configure trials, users, and projects.
-   Clarify customer expectations and workflow requirements.
-   Coordinate UAT and capture user feedback.
-   Record issues with reproducible steps and expected behaviour.
-   Communicate product gaps to Product, Engineering, and ML teams.
-   Support structured comparison of AI-generated outputs with reference
    materials.
-   Monitor trial progress and follow up on open questions.

## 4. Example validation method: relevance scoring

A scoring approach used in the described validation work assigns a value
to each assessed output:

    Score Meaning
  ------- --------------------
        2 Relevant
        1 Partially relevant
        0 Irrelevant

**Validation steps**

1.  Identify the workflow stage being evaluated.
2.  Select the appropriate reference material and test cases.
3.  Record the AI output and the expected/reference result.
4.  Apply the agreed relevance criteria consistently.
5.  Document mismatches and provide enough context for investigation.
6.  Track issues and retest when a correction becomes available.

**Acceptance criteria for a validation exercise**

-   [ ] Each test case is linked to a defined workflow stage.
-   [ ] The reference source is recorded.
-   [ ] The scoring definitions are available to reviewers.
-   [ ] Results are recorded consistently.
-   [ ] Discrepancies include the input, observed output, expected
    outcome, and supporting context.
-   [ ] Issues are routed to the relevant team.
-   [ ] Retest results are recorded separately from the initial result.

## 5. Example issue-report structure

  Field                What to record
  -------------------- --------------------------------------------------------
  Issue title          Concise description of the failure
  Environment          Trial/project and relevant configuration
  Preconditions        Data and settings needed to reproduce
  Steps to reproduce   Ordered, repeatable user actions
  Actual result        What the platform did
  Expected result      What should have happened
  Evidence             Screenshots or reference examples approved for sharing
  Impact               Effect on the workflow or research output
  Retest               Result after the fix or configuration change

## 6. Intended value

-   More structured AI workflow validation.
-   Better traceability between expected and observed outputs.
-   Clearer communication of customer feedback.
-   More actionable issue reports for Product, Engineering, and ML
    teams.

**Status note:** This case study describes product-support and
validation activities. It does not claim ownership of ML model
development or that validation results establish clinical or scientific
accuracy.

------------------------------------------------------------------------

# Case study 4 --- UAT, release coordination, and knowledge transfer

**Domain:** SaaS product delivery\
**Focus:** Release testing, issue tracking, documentation, and
operational handover\
**Work type:** Product administration and delivery coordination

## 1. Context

A consistent UAT process helps teams validate changes, communicate
defects, and keep release stakeholders aligned. During transition and
handover work, clear documentation is also needed so recurring tasks can
be performed consistently by another team member.

## 2. Example UAT workflow

``` text
Release tickets identified
          |
          v
Group tickets by feature / module
          |
          v
Prepare UAT scenarios
          |
          v
Execute tests and capture results
          |
          v
Report defects with reproduction steps
          |
          v
Coordinate with stakeholders
          |
          v
Retest fixes and update status
          |
          v
Share release / knowledge-transfer notes
```

## 3. Activities covered

-   Coordinating alternate-week UAT cycles and testing activities.
-   Downloading or collecting release tickets and organising them in a
    UAT Deployment Status tracker.
-   Documenting defects through the agreed team communication channel.
-   Comparing current behaviour, earlier behaviour, and relevant tickets
    to identify gaps.
-   Coordinating UAT and user-management-related communications.
-   Preparing release notes and material for SME knowledge-sharing
    sessions.
-   Explaining recurring administrative activities during handover,
    including activity logging, customer/user configuration, credit
    updates, and reporting.

## 4. Sample UAT test record

  -----------------------------------------------------------------------
  Field                               Example
  ----------------------------------- -----------------------------------
  Test ID                             UAT-001

  Requirement                         Saved article selection remains
                                      consistent

  Preconditions                       User has access to the relevant
                                      newsletter

  Steps                               Select multiple articles, add them,
                                      remove one, and revisit the section

  Expected result                     Selected articles and section
                                      contents reflect the user's actions

  Actual result                       Record the observed behaviour
                                      during execution

  Status                              Pass / Fail / Blocked --- populate
                                      after testing

  Defect reference                    Link the relevant ticket if a
                                      defect is raised
  -----------------------------------------------------------------------

This is a reusable template; the sample is not a record of an executed
test.

## 5. Acceptance criteria for a UAT coordination process

-   [ ] Each in-scope change has a corresponding test scenario or
    documented reason why testing is not applicable.
-   [ ] Test results are recorded against the relevant ticket.
-   [ ] Failed tests include reproduction steps and expected versus
    actual results.
-   [ ] Defects are linked to the affected requirement or release item.
-   [ ] Retest outcomes are recorded after a fix is available.
-   [ ] Blocked tests identify the dependency or missing prerequisite.
-   [ ] Release and handover notes identify outstanding items and the
    responsible follow-up team.

## 6. Intended value

-   Better visibility into UAT status.
-   More consistent defect reporting.
-   Improved continuity during handover.
-   Easier access to release decisions and outstanding work.

------------------------------------------------------------------------

# Selected requirements artefacts

The examples below illustrate how I structure requirements. They are
portfolio examples based on the types of work described above, not
copies of confidential internal tickets.

## Artefact A --- User story template

**Title:** `[Action] [Feature] to support [business outcome]`

**User story**

> As a \[user type\], I want to \[capability\], so that I can \[business
> value\].

**Description**

-   Current behaviour:
-   Problem / business need:
-   Expected behaviour:
-   In scope:
-   Out of scope:
-   Dependencies:
-   Open questions:

**Acceptance criteria**

-   Given \[precondition\], when \[action\], then \[expected outcome\].
-   Given \[alternative state\], when \[action\], then \[expected
    outcome\].
-   Given \[invalid or empty state\], when \[action\], then \[validation
    or empty-state behaviour\].

## Artefact B --- Defect ticket template

  Section               Details to capture
  --------------------- ----------------------------------------------
  Summary               One-sentence statement of the issue
  Environment           Relevant application area and environment
  Preconditions         Required user, data, settings or state
  Steps to reproduce    Numbered steps
  Actual result         Observed behaviour
  Expected result       Required behaviour
  Impact                User or business consequence
  Evidence              Approved screenshot or sample data
  Acceptance criteria   Observable conditions for resolution
  Regression scope      Related workflows that must continue working

## Artefact C --- Functional requirement template

  -----------------------------------------------------------------------
  ID                Requirement       Priority          Verification
  ----------------- ----------------- ----------------- -----------------
  FR-01             The user can      To be agreed      Search scenarios
                    search using the                    
                    agreed criteria.                    

  FR-02             The UI reflects   To be agreed      UI and result
                    the active                          comparison
                    criteria                            
                    accurately.                         

  FR-03             Invalid input     To be agreed      Negative tests
                    receives clear                      
                    feedback.                           

  FR-04             Existing          To be agreed      Regression tests
                    supported                           
                    workflows                           
                    continue to                         
                    function.                           
  -----------------------------------------------------------------------

Priority values and final requirements should be agreed with
stakeholders for each actual project.

------------------------------------------------------------------------

# Proposed mock case study --- Alert Statistics dashboard

**Classification:** Proposed redesign / mock ticket\
**Domain:** Alert administration and product analytics\
**Purpose:** Demonstrate how I turn a UI concept into functional scope
and acceptance criteria.

This is a proposed dashboard specification based on the Alert Statistics
mock ticket, not a claim that the redesign has been delivered.

## 1. Objective

Provide administrators with a central interface to search alert records,
analyse alert activity by company, recipient, and topic, and export
filtered results.

## 2. Proposed dashboard components

  -----------------------------------------------------------------------
  Component                           Proposed behaviour
  ----------------------------------- -----------------------------------
  Company search                      Search by customer/company name

  Alert-name search                   Filter by alert name

  Email search                        Filter by recipient email

  Alert type                          Scheduled and As-it-Happens filters

  Topic type                          Fullintel Topic, Admin My Topic, My
                                      Topic, AI Topic

  Date filter                         Today, Last Week, Last Month, with
                                      custom range if agreed

  Summary cards                       Top 3 companies, top 3 emails, top
                                      3 topics, total alerts

  Results table                       Company, subject, recipients,
                                      topic, alert type, interval, last
                                      sent time, elapsed time, status

  Export                              Export the filtered results

  Reset                               Clear user-applied filters and
                                      restore agreed defaults
  -----------------------------------------------------------------------

## 3. Sample acceptance criteria

-   [ ] Search criteria filter the displayed alert records correctly.
-   [ ] Summary cards reflect the filtered dataset.
-   [ ] Top-three rankings use the agreed count metric and tie-breaking
    rule.
-   [ ] The results table displays the required fields.
-   [ ] Scheduled alert intervals reflect the saved schedule.
-   [ ] The status indicator has a documented meaning and is not
    inferred from colour alone.
-   [ ] Exported data matches the active filters.
-   [ ] Reset clears the relevant user-applied filters.
-   [ ] Empty search results and export-with-no-data cases display clear
    messages.
-   [ ] Access to customer and recipient information follows the
    application's permission rules.

## 4. Questions to resolve before implementation

1.  Does "Total Alerts" mean configured alerts, successful sends, or all
    send attempts?
2.  What precisely determines an alert's status?
3.  How should alerts with multiple recipients contribute to the Top 3
    Emails metric?
4.  What timezone is used for last-sent timestamps?
5.  Should date filtering use alert creation date, last-sent date, or an
    execution-history date?
6.  Which roles can view and export recipient information?

These questions demonstrate an important BA practice: identifying
ambiguous metrics and business rules before development begins.

------------------------------------------------------------------------

# Additional product-analysis examples

These examples summarise other requirements and issues from my described
Fullintel work. They can be expanded into separate case studies when
supporting artefacts are available.

  -----------------------------------------------------------------------
  Area                    Problem / requirement   BA techniques
                          theme                   demonstrated
  ----------------------- ----------------------- -----------------------
  Prominence workflow     Edit prominence from a  State transitions,
                          real-time article       confirmation flow, data
                          preview, confirm before integrity, edge cases
                          saving, and add an      
                          updated copy to FI      
                          Curated while           
                          preserving the          
                          real-time article       

  Customer-specific       Ensure                  Business rules, scope
  outlet restrictions     customer-specific       analysis, regression
                          blocks do not affect    impact
                          unrelated customers and 
                          apply to the intended   
                          real-time section       
                          rather than FI Curated  

  Duplicate broadcast     Investigate duplicate   Problem investigation,
  clips                   results using clip      data consistency, test
                          metadata; hide          design
                          duplicates and align    
                          counts and downloads    

  Customer and user       Define customer-list    Functional
  administration          search, filters, action decomposition,
                          menus, user lists, DL   permissions, UI
                          groups and update       requirements
                          history                 

  Font-template setup     Preload standard fields Process improvement,
                          and allow an existing   configuration design,
                          font template to be     efficiency
                          duplicated rather than  
                          re-entering all values  

  NewsCatcher sentiment   Make sentiment          Data availability,
                          available for           integration
                          NewsCatcher articles in requirements,
                          Hub and Adhoc Search,   downstream impact
                          including               
                          transformation          
                          dependencies            
  -----------------------------------------------------------------------

For proposed or unverified items, I would label the portfolio entry as
**Proposed**, **In Progress**, or **Implemented and Verified** only when
the status can be substantiated.

------------------------------------------------------------------------

# How I measure success

I prefer to define measurable outcomes with stakeholders rather than
invent impact numbers.

  -----------------------------------------------------------------------
  Area                                Possible measure
  ----------------------------------- -----------------------------------
  Requirements quality                Number of clarification cycles or
                                      reopened tickets

  UAT effectiveness                   First-pass acceptance rate and
                                      defects found before release

  Workflow efficiency                 Time or number of actions needed to
                                      complete a task

  Search quality                      Percentage of results meeting the
                                      intended filter criteria

  Newsletter reliability              Output consistency across supported
                                      delivery methods

  Issue resolution                    Time from reproducible report to
                                      verified resolution

  AI validation                       Discrepancies recorded,
                                      categorised, and resolved against
                                      an agreed reference
  -----------------------------------------------------------------------

These are proposed measures. No numerical improvements are claimed here
because verified baseline and outcome data have not been supplied.

------------------------------------------------------------------------

# Confidentiality and evidence notes

This repository is intended for public professional presentation.

-   Do not upload proprietary source code, internal system screenshots,
    customer records, email addresses, private Jira links, credentials,
    or confidential product documentation.
-   Use anonymised or synthetic data in screenshots and examples.
-   Describe your individual contribution accurately and distinguish it
    from team delivery.
-   Do not label a proposed mock ticket as a shipped feature.
-   Add links to public demos or approved artefacts only when they are
    safe to share.
-   Where a project outcome is not measured, describe the intended
    business value rather than claiming a quantified result.

## Contact

**Business Analyst \| Product Administration \| SaaS & Requirements
Analysis**

-   LinkedIn: `[Add your LinkedIn URL]`
-   Email: `[Add a professional email address]`
-   Location / relocation: `[Add only if you wish to share publicly]`

*Thank you for reviewing my portfolio.*
