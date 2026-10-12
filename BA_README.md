# Business Analyst Portfolio

### Requirements Engineering · Product Analysis · SaaS Workflows · UAT

**Target roles:** Business Analyst · Product Analyst · Product
Operations Analyst\
**Domains:** Media Intelligence SaaS · Search & Monitoring · Newsletters
· Alerts · AI-Assisted Research\
**Tools:** Jira · Confluence · Excel · Google Sheets · ChatGPT · Claude
· Lovable · chatPRD

## About

My work spans requirements clarification, workflow analysis, Jira ticket
writing, issue investigation, UAT coordination, product administration,
and cross-functional communication. Fullintel-related examples cover
search, article management, newsletters, alerts, customer configuration,
and Hub workflows. MadeAI-related work covers trial setup, user/project
configuration, requirements clarification, UAT, issue reporting, and
validation of AI-assisted systematic literature review workflows.

**Important:** These are requirements artefacts based on tickets and
work described in previous conversations. Unless stated otherwise,
implementation and release status are not confirmed. Acceptance criteria
describe what should be verified; they do not claim that testing or
delivery has occurred.

## Contents

1.  [Second-Level Search Filters](#1-second-level-search-filters)
2.  [Duplicate Broadcast Clips](#2-duplicate-broadcast-clips)
3.  [Adhoc Search Date and Time](#3-adhoc-search-date-and-time)
4.  [Newsletter Sorting and
    Feedback](#4-newsletter-sorting-and-feedback)
5.  [Parent Articles and
    Syndications](#5-parent-articles-and-syndications)
6.  [NewsCatcher Sentiment](#6-newscatcher-sentiment)
7.  [Prominence Workflow](#7-prominence-workflow)
8.  [Font Template Redesign](#8-font-template-redesign)
9.  [Alert Statistics Dashboard](#9-alert-statistics-dashboard)
10. [Customer Administration UI](#10-customer-administration-ui)
11. [Additional Ticket Inventory](#additional-ticket-inventory)
12. [BA Validation Checklist](#ba-validation-checklist)

------------------------------------------------------------------------

# 1. Second-Level Search Filters

**Product area:** Search / OneSearch\
**Artefact type:** Functional enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

Users need to refine search results by article metadata. The requested
filters should provide counts for available values and allow users to
select or deselect criteria, similar to the filtering experience in the
LexisNexis platform.

## User story

As an analyst, I want to filter search results by article metadata and
see the count for each filter value, so that I can narrow broad results
to relevant articles.

## Scope

Required filter groups: **Source, Source Country, Source Rank, Reach,
Media Type, Language, Tonality, Source Type.**

## Functional requirements

-   **FR-01 --- Filter groups:** Display all eight filter groups.
-   **FR-02 --- Metadata counts:** Display a count beside each available
    filter value, based on article metadata.
-   **FR-03 --- Apply:** Selecting a value updates the result set.
-   **FR-04 --- Deselect:** Removing a selected value updates the result
    set.
-   **FR-05 --- Combine:** Support simultaneous filters across groups
    according to agreed AND/OR rules.
-   **FR-06 --- State consistency:** Keep selected states, counts, and
    displayed results consistent.
-   **FR-07 --- Empty state:** Show a clear message when no articles
    match.

## Acceptance criteria

-   [ ] All eight required filter groups are displayed.
-   [ ] Filter values and counts are based on the agreed article
    metadata and counting rules.
-   [ ] Selecting a value applies that filter and refreshes results.
-   [ ] Deselecting a value removes that constraint.
-   [ ] Multiple filters can be applied together according to documented
    combination rules.
-   [ ] Selected and unselected values are visually distinguishable.
-   [ ] No-match results show an empty state rather than a misleading
    error.
-   [ ] Existing query, date-range, and search-source behaviour remains
    functional.

## Edge cases

-   Missing metadata; empty filter group; zero-count value; multiple
    values in one group; filters combined across groups; changed result
    set after a new search.

## Questions to resolve

1.  Are values within one group combined using OR and groups combined
    using AND?
2.  Are counts calculated against all query results or recalculated
    after other filters?
3.  Are all groups multi-select?
4.  Do selections persist after changing the query or date range?

------------------------------------------------------------------------

# 2. Duplicate Broadcast Clips

**Product area:** Analyst End → Adhoc Search; Hub Historical Search\
**Artefact type:** Defect investigation and enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

Duplicate broadcast clips were reported in Adhoc Search and Hub
Historical Search. The source data comes from TVEyes, and callsigns can
differ between records. The requirement is to analyse clip metadata,
hide duplicates in the UI, and align the displayed count and downloads
with the unique result set.

## User story

As an analyst, I want duplicate broadcast clips to be identified and
hidden, so that I can review and download an accurate set of unique
clips.

## Reproduction steps

1.  Open Analyst End → Adhoc Search.
2.  Run the broadcast query from the original issue.
3.  Inspect returned clips for duplicate entries.
4.  Open the relevant customer's Hub and navigate to Historical Search.
5.  Apply the reported TV-article filter and compare results.
6.  Compare clip metadata, including callsign and any available clip
    identifiers.

The original report referenced customer IDs 666 (Archdiocese of Chicago)
and 521 (Vision). Use approved test access and avoid publishing customer
data.

## Functional requirements

-   Analyse available TVEyes metadata to establish a reliable
    duplicate-identification rule.
-   Show only one entry for records confirmed to represent the same
    clip.
-   Calculate the displayed result count from unique clips.
-   Apply the same deduplication rule to downloads.
-   Preserve distinct clips that share only non-unique metadata.

## Acceptance criteria

-   [ ] The deduplication rule and metadata fields are documented.
-   [ ] The rule addresses duplicate records with differing callsigns
    where the available metadata supports it.
-   [ ] Confirmed duplicates appear once in the relevant UI.
-   [ ] The displayed count matches the number of unique results.
-   [ ] Downloads do not include hidden duplicates as separate entries.
-   [ ] Distinct clips are not merged incorrectly.
-   [ ] Both Adhoc Search and the specified Hub workflow are tested.
-   [ ] Other media types and unrelated results remain unaffected.

## Edge cases and questions

-   Same clip, different callsigns; same callsign, different clips;
    missing identifiers; similar titles at different times; duplicates
    across pages; UI/export count mismatch.
-   Which fields establish clip identity? Which duplicate record is
    retained? Is deduplication global to TVEyes or limited to this
    workflow?

------------------------------------------------------------------------

# 3. Adhoc Search Date and Time

**Product area:** Analyst End → Adhoc Search\
**Artefact type:** Defect ticket\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

A reported search used station **CTV Atlantic (CKLT)**, date
**17-02-2026**, start time **15:50:02**, end time **16:00:17**, and no
Boolean query. Two results were returned, but the clips appeared to
start around 15:55 and end around 16:05, outside the selected window.

## User story

As an analyst, I want broadcast search results to respect my selected
station, date, start time, and end time, so that I can retrieve clips
from the intended period.

## Steps to reproduce

1.  Log in to Analyst End and open Adhoc Search.
2.  Select station `CTV Atlantic (CKLT)`.
3.  Set date to `17-02-2026`.
4.  Set start time to `15:50:02` and end time to `16:00:17`.
5.  Leave Boolean input empty and run the search.
6.  Inspect the timestamps of returned clips.

## Requirements

-   Apply the selected station and date.
-   Apply start and end times to the authoritative timestamp field, to
    be confirmed with Engineering.
-   Reflect the applied criteria accurately in the UI.
-   Preserve the supported search-without-Boolean workflow.

## Acceptance criteria

-   [ ] Results use the selected station and date.
-   [ ] The selected time window is applied to the agreed timestamp
    field.
-   [ ] Clips outside the agreed time-window rule are excluded.
-   [ ] Boundary behaviour at the start and end time is documented and
    tested.
-   [ ] Displayed criteria match the criteria applied to results.
-   [ ] Search without Boolean input works as expected.
-   [ ] No-match results display a clear empty state.
-   [ ] Existing station and date filtering remains functional.

## Questions to resolve

-   Is inclusion based on clip start, clip end, broadcast time, or
    another timestamp?
-   Are start and end boundaries inclusive?
-   Which timezone applies?
-   Should a clip that overlaps the window but begins before it be
    included?

------------------------------------------------------------------------

# 4. Newsletter Sorting and Feedback

**Product area:** Analyst End → Newsletter creation → Settings\
**Artefact type:** Existing-sort defect fix plus enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

Existing alphabetical, date, and reach sorting options were reported as
not working in production. New sorting options were requested for
content types/topics in ascending and descending order. The selected
sort should take effect when the user clicks Update. Tooltips and toast
messages were also requested.

## User story

As an analyst, I want to sort newsletter content by title, date, reach,
or topic name, so that I can organise the newsletter consistently.

## Scope

-   Alphabetical ascending and descending
-   Date ascending and descending
-   Reach ascending and descending
-   New: Topics A--Z and Topics Z--A
-   Tooltips and success/error toast feedback

## Functional requirements

-   **FR-01:** User selects a sort option in Settings.
-   **FR-02:** Clicking Update applies the selected sort.
-   **FR-03:** Alphabetical sort uses article title.
-   **FR-04:** Date sort uses the agreed article-date field.
-   **FR-05:** Reach sort orders by reach value.
-   **FR-06:** Topics A--Z / Z--A orders content types by topic name.
-   **FR-07:** Each option has a descriptive tooltip.
-   **FR-08:** Toast feedback appears only after the operation's outcome
    is known.

## Suggested tooltip and toast copy

  -----------------------------------------------------------------------
  Option                  Tooltip                 Success toast
  ----------------------- ----------------------- -----------------------
  Alphabetical A--Z       Sort articles by title  Articles sorted by
                          in ascending            title: A--Z.
                          alphabetical order.     

  Alphabetical Z--A       Sort articles by title  Articles sorted by
                          in descending           title: Z--A.
                          alphabetical order.     

  Date ascending          Sort articles from      Articles sorted by
                          oldest to newest.       date: oldest to newest.

  Date descending         Sort articles from      Articles sorted by
                          newest to oldest.       date: newest to oldest.

  Reach ascending         Sort articles from      Articles sorted by
                          lowest to highest       reach: low to high.
                          reach.                  

  Reach descending        Sort articles from      Articles sorted by
                          highest to lowest       reach: high to low.
                          reach.                  

  Topics A--Z             Sort content types by   Topics sorted by name:
                          topic name in ascending A--Z.
                          alphabetical order.     

  Topics Z--A             Sort content types by   Topics sorted by name:
                          topic name in           Z--A.
                          descending alphabetical 
                          order.                  
  -----------------------------------------------------------------------

## Acceptance criteria

-   [ ] All six existing sort options work correctly.
-   [ ] Topics A--Z and Topics Z--A are available.
-   [ ] Topic sorting uses content type/topic name, not article title.
-   [ ] The selected sort is applied after Update.
-   [ ] Sorting does not remove or alter article content.
-   [ ] Each option displays the correct tooltip.
-   [ ] Success toast appears only after successful application.
-   [ ] Failed application displays an error and no false success toast.
-   [ ] Equal values are handled with an agreed secondary sort.
-   [ ] Existing newsletter actions continue to work.

## Questions to resolve

-   What secondary sort applies when values are equal?
-   Does sort selection persist after reopening the newsletter?
-   Does the toast appear after client-side sorting or after server
    confirmation?

------------------------------------------------------------------------

# 5. Parent Articles and Syndications

**Product area:** Analyst End → Adhoc Search → Newsletter\
**Artefact type:** Workflow enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

The requested behaviour mirrors the display of syndications in the
Alerts feature. Syndicated articles should be shown beneath their parent
article. When the parent is added to a newsletter, its associated
syndications should also be added, reducing manual tagging.

## User story

As an analyst, I want syndications grouped under a parent article and
added with the parent in one action, so that I can reduce repetitive
newsletter tagging.

## Functional requirements

-   Display syndicated articles below the parent.
-   Show `Syndications (x):`, where `x` is the number of associated
    syndications.
-   Adding the parent adds its associated syndications to the
    newsletter.
-   Avoid creating duplicate newsletter entries when a syndication is
    already present.
-   Preserve the existing workflow for articles without syndications.

## Acceptance criteria

-   [ ] Parent articles with syndications show `Syndications (x):`.
-   [ ] The count matches the associated syndications.
-   [ ] Syndications appear beneath the correct parent.
-   [ ] Adding the parent also adds associated syndications.
-   [ ] Articles without syndications remain addable as before.
-   [ ] Already-added syndications are not duplicated.
-   [ ] The newsletter contains the expected set of articles after the
    action.
-   [ ] Tests cover zero, one, and multiple syndications.

## Questions to resolve

-   Can the syndication list expand/collapse?
-   Should already-added syndications be skipped silently or reported?
-   What happens if a syndication is unavailable at the time of adding?

------------------------------------------------------------------------

# 6. NewsCatcher Sentiment

**Product area:** Fullintel Hub and Adhoc Search\
**Artefact type:** Data availability enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

Sentiment was reported as unavailable for NewsCatcher articles in Hub
and Adhoc Search. The original technical discussion indicated that the
NewsCatcher transformation logic needed to expose sentiment. Sentiment
is important for use cases such as sentiment-based automated alerts.

## User story

As a media-intelligence user, I want sentiment available for NewsCatcher
articles in Hub and Adhoc Search, so that I can review sentiment
consistently and support downstream sentiment-based workflows.

## Functional requirements

-   Investigate the NewsCatcher transformation logic required to expose
    sentiment.
-   Make the agreed sentiment field available to the backend and
    frontend.
-   Display sentiment in Hub article cards where supported.
-   Display sentiment in Adhoc Search where supported.
-   Ensure UI values match the backend response.
-   Handle missing or unavailable sentiment explicitly.

## Acceptance criteria

-   [ ] Eligible NewsCatcher articles expose the agreed sentiment field.
-   [ ] The backend returns the field for eligible records.
-   [ ] Hub displays the returned value consistently.
-   [ ] Adhoc Search displays the returned value consistently.
-   [ ] Missing values are not shown as a fabricated sentiment.
-   [ ] Other source types retain existing behaviour.
-   [ ] Article loading and search remain functional.
-   [ ] Availability for future sentiment-based alert logic is
    confirmed, with alert filtering scoped separately if needed.

## Questions to resolve

-   What values are allowed (e.g. Positive, Negative, Neutral,
    unavailable)?
-   Is sentiment provided by NewsCatcher or derived during
    transformation?
-   Does the change cover historical records as well as newly ingested
    articles?
-   Is sentiment-based alert filtering included or a separate ticket?

------------------------------------------------------------------------

# 7. Prominence Workflow

**Product area:** Search & Monitor → Topic/subtopic → Realtime → Article
preview → FI Curated\
**Artefact type:** Proposed workflow enhancement\
**Status:** Requirement documented; delivery status unconfirmed

## Business context

The requested workflow lets a user edit an article's prominence from the
Realtime tab. After confirmation, the updated version should be listed
in FI Curated as a copy, while the original Realtime article remains
unchanged.

## User story

As a user managing a topic's articles, I want to update prominence from
the article preview and save the revised version to FI Curated, so that
I can curate a modified copy without changing the original Realtime
article.

## Workflow

``` text
Open topic/subtopic
       |
       v
Select Realtime tab
       |
       v
Hover over article → click Edit
       |
       v
Article preview opens
       |
       v
Update prominence → click Save
       |
       v
Confirmation prompt
    /          \
 Cancel       Confirm
   |             |
No change    Save curated copy
                 |
                 v
       Realtime original unchanged
       Updated copy listed in FI Curated
```

## Proposed confirmation message

**Title:** Save prominence update?

**Message:** Your prominence changes will be saved to FI Curated as a
separate copy. The original Realtime article will remain unchanged.

**Actions:** Cancel · Confirm Save

## Functional requirements

-   Hovering over an eligible Realtime article reveals the edit action.
-   Edit opens the corresponding article preview.
-   The user can change prominence.
-   Save triggers a confirmation prompt before committing the change.
-   Confirming saves the revised version to FI Curated as a copy.
-   The original Realtime article remains unchanged.
-   The UI provides success or failure feedback.

## Acceptance criteria

-   [ ] The edit action appears on hover for eligible articles.
-   [ ] Edit opens the correct article preview.
-   [ ] The user can update prominence and review the value before
    saving.
-   [ ] Save opens the confirmation prompt.
-   [ ] Cancel leaves the record unchanged and creates no curated copy.
-   [ ] Confirm creates or updates the intended FI Curated copy.
-   [ ] The Realtime original remains unchanged.
-   [ ] FI Curated displays the updated prominence.
-   [ ] Success feedback appears only after a successful save.
-   [ ] Failure feedback appears if saving fails.
-   [ ] Repeated saves do not create unintended duplicate copies.

## Questions to resolve

-   Should each save create a new copy or update an existing curated
    copy?
-   Which original article fields are copied?
-   Is an audit trail required?
-   Which roles can edit prominence?

------------------------------------------------------------------------

# 8. Font Template Redesign

**Product area:** Admin Backend → Customize → Customize Newsletter Font\
**Artefact type:** New-application redesign / mock ticket\
**Status:** Proposed redesign; not represented as delivered

## Business context

Before creating a new customer in the backend application, font
customisation must be set up. The current process requires manual entry
for approximately 35 fields, including label, font style, colour,
weight, size, unit, and background colour. Users also have to change
font units to `px` and cannot duplicate an existing template.

## User story

As an administrator, I want font fields preloaded and an option to
duplicate a template, so that I can configure a new customer's
newsletter styling with less repetitive data entry.

## Functional requirements

-   Preload all supported font-configuration fields.
-   Expose the relevant properties: Field Label Name, Font Style, Font
    Color, Font Weight, Font Size, Font Unit, Background Color.
-   Default Font Unit to `px` where applicable.
-   Allow users to duplicate an existing template.
-   Allow edits to the duplicate without changing the original.
-   Save the modified copy as a new template.
-   Validate required fields and invalid values.

## Acceptance criteria

-   [ ] All standard configurable fields are preloaded.
-   [ ] Users do not need to manually create each standard field.
-   [ ] Applicable Font Unit fields default to `px`.
-   [ ] A user can duplicate an existing template.
-   [ ] Editing a duplicate does not alter the original.
-   [ ] The duplicate can be saved as a separate template.
-   [ ] Invalid values and required-field omissions receive clear
    validation.
-   [ ] Reopening the saved template shows the saved configuration.
-   [ ] Existing template/customer setup workflows remain supported.

## Questions to resolve

-   Which template is the default starting point?
-   Which fields should be copied or reset?
-   Must template names be unique?
-   Is a rendered preview required?
-   Are there customer-level permissions or restrictions?

------------------------------------------------------------------------

# 9. Alert Statistics Dashboard

**Product area:** Alerts → Alert Statistics\
**Artefact type:** Mock ticket / proposed redesign\
**Status:** Proposed mock, not a delivered feature claim

## Objective

Provide a central interface to search alert activity and review summary
metrics by company, email recipient, topic, alert type, and time period.

## Proposed components

  -----------------------------------------------------------------------
  Component                           Proposed behaviour
  ----------------------------------- -----------------------------------
  Company                             Search by company name

  Search by alert name                Filter by alert name

  Search by email                     Filter by recipient email

  Alert type                          Scheduled Alerts / As-it-Happens
                                      Alerts

  Topic type                          Fullintel Topic / Admin My Topic /
                                      My Topic / AI Topic

  Date controls                       Relative periods such as Today,
                                      Last Week, Last Month; date range
                                      as supported

  Summary cards                       Top 3 Companies, Top 3 Emails, Top
                                      3 Topics, Total Alerts

  Results table                       Company ID & Name, Subject Line,
                                      Recipients, Topic Name, Alert Type,
                                      Alert Time Interval, Last Sent Date
                                      & Time, Hours Difference, Status

  Search                              Apply selected criteria

  Export                              Export filtered results

  Reset                               Clear filters and restore agreed
                                      defaults
  -----------------------------------------------------------------------

## Functional requirements

-   Search by company, alert name, and recipient email.
-   Filter by alert type and topic type.
-   Select a relative period or supported custom date range.
-   Apply search criteria to table rows and summary cards according to
    agreed metric rules.
-   Rank the top-three company, email, and topic cards using a defined
    count metric.
-   Export the filtered dataset.
-   Reset filters.
-   Give status indicators a documented meaning; do not rely on colour
    alone.

## Acceptance criteria

-   [ ] Search applies the selected criteria to the displayed records.
-   [ ] Summary cards use the agreed filtered dataset and metric
    definitions.
-   [ ] Top-three values follow documented ranking and tie-breaking
    rules.
-   [ ] The table displays all requested columns.
-   [ ] Date filters use an agreed timestamp and timezone.
-   [ ] Exported rows match the active filters.
-   [ ] Reset restores the documented default state.
-   [ ] Empty results and empty exports are handled clearly.
-   [ ] Customer and recipient data follows existing access permissions.

## Questions to resolve

1.  Does Total Alerts count configured alerts, deliveries, or send
    attempts?
2.  Does the date filter use creation date or last-sent date?
3.  How are recurring schedules displayed?
4.  How are alerts with multiple recipients counted in Top 3 Emails?
5.  What do status values mean?
6.  What is the default date range and timezone?

------------------------------------------------------------------------

# 10. Customer Administration UI

**Product area:** Admin application → Customer List\
**Artefact type:** UI requirements / proposed screen\
**Status:** Requirement documented; delivery status unconfirmed

## Customer List

**Header:** Customer List and `+ Create` action.

**Search and filters:** - Search by customer name; exact and partial
match. - Filter by Name, Status, Modified Date. - Status options: Active
/ Inactive.

**Table columns:** - Logo - Customer ID - Customer Name (full name
visible; A--Z sorting) - License - Users - Status - Action

**Per-customer action menu:** - Manage Associated Companies - Manage DL
Groups - Manage Control Options - Edit Company - View Users - Update
History

## Manage Associated Companies

Display the companies associated with the selected customer.

## Manage DL Groups

**Filters/search:** Name, Status; Contains or Exact match; order by Name
or Created Date.

**Group actions:** Create, Delete, Import, Export, Download Format.

**User search:** First Name, User ID, keyword search, Subscribed Yes/No.

**User table:** Select All, First Name, Last Name, Email, Created Date,
Subscribed, Edit.

**Pagination:** Page numbers and range text such as `Showing 1–100`.
Selected page uses red background and white text, as requested.

## View Users

-   Customer name in the header.
-   Close control.
-   Search by User Name or User ID.
-   `+ New` action.
-   Table: Name, User ID, Status, Last Login.
-   Pagination with visible page numbers and record-range text.

## Update History

-   User Name
-   Edit Done
-   Last Modified Date & Time
-   Pagination with visible page numbers and record-range text.

## Acceptance criteria

-   [ ] Customer search supports exact and partial matches.
-   [ ] Filters apply to the customer list.
-   [ ] Customer names can be sorted A--Z.
-   [ ] Active/Inactive filtering works.
-   [ ] Each action menu item opens the corresponding screen.
-   [ ] Associated-company view shows companies linked to the selected
    customer.
-   [ ] DL Group filters and search apply the selected conditions.
-   [ ] DL Group user search supports the specified fields and
    subscribed state.
-   [ ] Create/edit/delete/import/export actions respect permissions.
-   [ ] View Users displays the selected customer's context and
    requested fields.
-   [ ] Update History displays the requested audit fields.
-   [ ] Pagination and range labels match the displayed records.
-   [ ] Empty states and action failures are communicated clearly.

## Questions to resolve

-   How are License and Users values calculated?
-   What confirmation is required before deleting a DL group or
    customer?
-   Which roles can access each action?
-   Is Modified Date date-only or date-time?
-   Is multi-column sorting required?

------------------------------------------------------------------------

# Additional Ticket Inventory

These are other requirements from my described work. They are listed to
show the breadth of product analysis, not to claim completion.

  -----------------------------------------------------------------------
  Area                    Requirement / issue     Artefact type
  ----------------------- ----------------------- -----------------------
  Adhoc Search            Strict selected-domain  Search enhancement
                          filtering for           
                          NewsCatcher and         
                          Online/Print            

  Adhoc Search            Wildcard and            Defect analysis
                          fuzzy-search syntax not 
                          working                 

  Adhoc Search            Download filenames      Usability enhancement
                          based on saved search   
                          name and date           

  Historical Search       AI summarisation of     Proposed enhancement
                          articles                

  Hub Alerts              Differentiate           UI enhancement
                          NewsCatcher and         
                          LexisNexis source types 

  Hub                     Article edits refresh   Data/UI consistency
                          article card without    defect
                          requiring preview       

  Hub                     Duplicate topic labels  Data consistency
                          and counts after        investigation
                          spreadsheet edits and   
                          RSS-folder movement     

  Gilead template         Related and syndicated  Template/output issue
                          articles missing from   
                          Gilead Europe website   
                          output                  

  Newsletter              Increase manual summary Editor enhancement
                          limit to 20,000+        
                          characters              

  Newsletter              Key Insight fields per  Settings/template
                          Gilead content type     enhancement

  Newsletter              Hide empty content      Rendering rules
                          types/categories in     
                          output                  

  Newsletter              Consistent section      Workflow defect
                          order across test,      
                          download, and send      

  Media types             Add Threads and Bluesky Configuration/data
                          and reflect them in     enhancement
                          supported outputs       

  Outlet restrictions     Customer-specific       Business-rule defect
                          blocks must not affect  
                          other customers or FI   
                          Curated                 

  MadeAI                  Trial setup,            Product operations
                          project/user            
                          configuration, UAT,     
                          issue reporting         

  MadeAI                  Validation across       AI workflow validation
                          protocol, screening,    
                          extraction, risk of     
                          bias, synthesis         
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# BA Validation Checklist

## Before development

-   [ ] Business problem and user impact are clear.
-   [ ] Current and expected behaviour are separated.
-   [ ] Scope and exclusions are stated.
-   [ ] Business rules and dependencies are identified.
-   [ ] Data fields and authoritative sources are identified where
    needed.
-   [ ] Ambiguities are captured as open questions.
-   [ ] Acceptance criteria are observable and testable.

## During testing and delivery

-   [ ] Original reproduction steps are tested.
-   [ ] Positive, negative, boundary, and empty-state cases are
    considered.
-   [ ] Related workflows are checked for regression.
-   [ ] UI counts, records, and downloads are consistent where
    applicable.
-   [ ] Defects include actual versus expected behaviour.
-   [ ] Retest outcomes are recorded.
-   [ ] Delivery status is verified before describing a ticket as
    complete.


## Contact

**Business Analyst \| Product Administration \| SaaS & Requirements
Analysis**

-   LinkedIn: `https://www.linkedin.com/in/cibinoross/`
-   Email: `cibinoross@gmail.com`
-   GitHub: `https://github.com/cibinoross/business-analyst-portfolio`

*This portfolio demonstrates requirements analysis, functional
decomposition, acceptance-criteria writing, and test-oriented thinking.*
