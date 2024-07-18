# IBM OpenPages
## About OpenPages

IBM OpenPages® is an AI-driven, highly scalable governance, risk, and compliance (GRC) solution. OpenPages enables organizations to centralize siloed risk management functions within a single environment to identify, manage, monitor, and report on risk and regulatory compliance. 

### Reporting Fragments
A reporting fragment is typically either a chart, crosstab or list that can be placed on a page of the application so that the user can see a visual representation of data alongside the page data.

### Using Images in Reporting Fragments
 You can insert an image in a report that is used in Reporting Fragments.
The images that you insert must first be uploaded to both the IBM® Cognos® Analytics server and the IBM OpenPages® server. Images must be gif or jpg format.

After you upload the image, you must use a relative path to refer to the image. The relative path should be valid on both the IBM Cognos Analytics server and the IBM OpenPages server.
Follow these best practices:
- Copy the image to the following folders:
  - `<COGNOS_HOME>\webcontent\bi\images`
  - `<OP_HOME>/wlp-usr/shared/apps/op-apps.ear/sosa.war/images`
- Access the image in the report that is used for the reporting fragment by using the relative path ../images/<image file name>.

### Framework Models
OpenPages® includes a set of framework models. The following table lists the models and their namespaces.

|  Model |  Description | Namespaces |
|---|---|---|
| Assurance and Testing | For audit and assurance management use cases | AUD1, AUD2, DEFAULT |
| Model Risk and Data Privacy | For model risk and data privacy use cases | DEFAULT, DPM1, MRG1, MRG2  |
| Operational Risk and Control | For operational risk and financial control management use cases | DEFAULT, ORM1, ORM2, ORM3, RA1, RA2, SOX1 |
| Policy and Compliance | For regulatory and policy management use cases | DEFAULT, MAND1, MAND2, POL1, RCM1, RCM2, RCM3, REGAPP1 |
| Resilience and Continuity | For IT governance, business continuity, third party management, and operational resilience use cases | BCM1, BCM2, BCM3, BCM4, BCM5, BCM6, BCM7, BCM8, BCM9, DEFAULT, ITG1, ITG2, TPRM1 |
| Platform Reporting | The Level 0 framework model, which is used to run platform reports | DEFAULT |

### Object naming conventions
Use the following conventions to name objects:
- The maximum length of an object name is 252 characters.
- Only single spaces are allowed.
- If auto-naming is enabled, the name of the object is automatically created.
- Only the following special characters are allowed: ~@^()_+`[]{};',.!#%&*,'<>:"|?
    The forward slash / and backward slash \ are not allowed.
- The name must be unique within a folder.

If the Title field is enabled for an object type, use the following conventions:
- The object ID must meet the requirements for object names.
- The maximum length of an object Title is 4,000 characters.

### Optimize Report performance
  - Filtering Top Level Business Entities: To improve the performance of a report,
    all reports should either have a prompt that filters to a specific business entity
    or a filter that scopes the report by the top level business entity or entities.
    If reports are run without being scoped to a single entity, the query performs multiple
    searches through the hierarchy. This slows down the response time greatly and may introduce
    undesirable results for the entity prompt query page or report.
  - Filtering on Reporting Periods: All reports should include a filter on the reporting period.
    A reporting period is a snapshot of all of the data in your database as a function of time.
    This creates a very large data set each time this operation is performed.
  - Bypassing an Index: In the database tables, indexes are defined on all the enumerated string
    value IDs. If you use enumerated string value IDs as filters, you might want to bypass the specific
    index on the field for better performance overall.
  - Query Direction Performance: When you explore all the computation possibilities, there is one large
    distinction in what you can and should do
  - Adding New Indexes: If you find that a pattern in your reports involves joining two fields that are not indexed,
    it is worthwhile investigating whether adding the index will improve the report’s performance.
  - The Use for Parameter Info Setting: You can set the Use for Parameter Info property on all query subjects.
  

### Creating Graphs in a Report
1. To create a new chart report, complete the following steps.
  - Select the Pie, Donut Chart grouping.
  - Select the Pie chart type.
  - Click OK.
2. Drag and drop the following query items into the various chart sections:
   - Categories (pies)
        ```DEFAULT|[DEFAULT_REL]|GRC_OBJECTS|SOXBUSENTITY_FOLDER|
        [SOXBUSENTITY_GPC]|[SOXBUSENTITY_GPC]|[CEN_NAME00]
        ```
   - Default Measures
        ```
        DEFAULT|[DEFAULT_REL]|GRC_OBJECTS|[SOXCONTROL]|ID_FIELDS|
        [CN_CONTROL_ID]
        ```
   - Series (pie slices)
     ```
     DEFAULT|[DEFAULT_REL]|GRC_OBJECTS|[SOXCONTROL]|ENUMERATION_FIELDS|
     ```
3. From the Query Explorer, select the query.
4. In the Properties pane under Miscellaneous, set the name of the query to chartMain.
5. In the Data Items pane, select [CN_CONTROL_ID] and complete the following steps.
   - In the Properties pane under Data Item, change the value of the Aggregate Function property to Count Distinct.
   - In the Properties pane under Data Item, change the value of the Rollup Aggregate Function property to
    Automatic.
6. From the Page Explorer, create a Prompt Page and create a Business Entity prompt as shown in Adding a Business
  Entity Prompt.
1. Return to the main report page.
2. Double-click the title and set the value to Operating Effectiveness.
3. Run the report.
