# CDS Topology

### Table of Contents
**[1 Introduction](#introduction)**<br>
**[2 Topology Layers](#topology-layers)**<br>
**[3 Logical Layer](#logical-layer)**<br>
**[3.1 CDS Object Tree](#cds-object-tree)**<br>
**[3.2 CDS and SQL](#cds-and-sql)**<br>
**[3.3 CDS System Function](#cds-system-function)**<br>
**[3.4 CDS Scalar Function and CDS Table Function](#cds-scalar-function-and-cds-table-function)**<br>
**[3.5 CDS System Entities](#cds-system-entities)**<br>
**[4 Linguo-Technical Layer](#linguo-technical-layer)**<br>
**[4.1 Mapping CDS Language to CDS Source Code and CDS Object](#mapping-cds-language-to-cds-source-code-and-cds-object)**<br>
**[5 Syntactic Layer](#syntactic-layer)**<br>
**[5.1 CDS by Keyword](#cds-by-keyword)**<br>
**[5.2 Keyword Semantic](#keyword-semantic)**<br>
**[6 Business Layer](#business-layer)**<br>
**[6.1 VDM Type](#vdm-type)**<br>
**[6.2 CDS Purpose](#cds-purpose)**<br>
**[6.3 CDS by Stability Contract](#cds-by-stability-contract)**<br>
**[6.4 CDS by Lifecycle](#cds-by-lifecycle)**<br>
**[6.5 CDS by Modelling Pattern](#cds-by-modelling-pattern)**<br>

## Introduction

Recently, I reviewed the ABAP keyword documentation to get an overview of the CDS framework from a high-level perspective. I came across numerous terms, each defined in the keyword dictionary. For example, terms like **CDS Objects**, **DDL**, and **CDS Entity** were mentioned, among others.

This prompted me to organize and systematize these terms to better understand their roles and why the documentation authors chose to highlight them.

As a result, I came up with the idea of creating a CDS classification. Of course, this topology is not exhaustive.

This article turned out to be quite a long read, and I hope, dear reader, that you won’t mind. Maybe you’ll find a moment to go through this classification while sipping your latte on a winter evening. Otherwise, feel free to use the table of contents above to navigate quickly through the article.

I’ve only gathered high-level information here, so I encourage you to dive deeper if you're interested.

## Topology Layers

The CDS typology begins by dividing the CDS framework into four layers:

1 **Logical**<br>
2 **Linguo-technical**<br>
3 **Syntactic**<br>
4 **Business**<br>

The first three layers are derived from the keyword documentation, while the fourth—**Business**—is based on my experience working with the CDS framework.

## Logical Layer

At the foundation of the **Logical level** is the term **CDS object**. I would define a CDS object as a programmatic entity that encapsulates all runtime properties of a CDS view. We refer to a CDS as an object when it is used as a type in ABAP code, as part of an Open SQL selection, or in similar contexts.

### CDS Object Tree

I would represent CDS objects as the following tree:

1 **CDS objects**<br>

1.1 **CDS annotations**<br>

1.2 **CDS metadata extensions**<br>

1.3 **CDS entities**<br>
1.3.1 **CDS view entities**<br>
1.3.2 **CDS projections view**<br>
1.3.2.1 **CDS Transactional query**<br>
1.3.2.2 **CDS Analytical projection view**<br>
1.3.2.3 **CDS Transactional interface**<br>
1.3.3 **CDS Table functions**<br>
1.3.4 **CDS Hierarchies**<br>
1.3.5 **CDS Custom Entities**<br>
1.3.6 **CDS Abstract Entities**<br>
1.3.7 **CDS DDIC-based views**<br>
1.3.8 **CDS External Entities**<br>
1.3.9 **ABAP CDS Aspect**<br>

1.4 **CDS Tunning Objects**<br>
1.4.1 **CDS Entity Buffers**<br>

1.5 **CDS User Defined Types**<br>
1.5.1 **CDS Simple Types**<br>
1.5.2 **CDS Enumeration Types**<br>

1.6 **CDS Functions**<br>
1.6.1 **CDS Scalar Functions**<br>
1.6.1.1 **CDS SQL-based Scalar Functions**<br>
1.6.1.2 **CDS Analytical Scalar Functions**<br>
1.6.2 **CDS Built-in Functions**<br>

1.7 **CDS Roles**<br>

### CDS and SQL

Also, it's worth to mention It is also worth mentioning the classification of **CDS Entities** into two categories:

1. **CDS SQL Entities** – This includes all entities except CDS non-SQL entities.


2. **CDS Non-SQL Entities** – These are specialized entities such as **Abstract Entities**, **Custom Entities**, and **CDS Analytical Projection Views**.

### CDS System Function

Another important aspect to clarify is the semantic overlap between **CDS user-defined functions** and **CDS system functions**. The overarching term for both is **CDS Scalar Function**, which can be further classified as follows:

1. **CDS Scalar Function**<br>
1.1 **Analytical Scalar Function** - Classified as a **System Function**<br>
1.2 **SQL-Based Scalar Function**<br>
    1.2.1 **Delivered by SAP** - Classified as a **System Function**<br>
    1.2.2 **User-Defined Scalar Function**<br>

### CDS Scalar Function and CDS Table Function

I would also like to emphasize the dichotomy between **CDS Table Functions** and **CDS Scalar Functions**. While **CDS Table Functions** are classified as a type of **CDS Entity**, **CDS Scalar Functions** fall under the category of **CDS Functions**.

### CDS System Entities

Lastly, it’s worth noting that SAP provides special **CDS System Entities**, which are predefined entities. However, for the sake of clarity and consistency, I propose classifying them under **CDS Entities**, specifically as entities delivered by SAP.

## Linguo-Technical Layer

At the core of the **Technical level** lies the term **CDS source code**. Why is this significant? The answer is that CDS source code is used by developers to define all the properties of a CDS object. Additionally, it serves for transporting CDS objects between systems and generating the corresponding runtime artifacts.

### Mapping CDS Language to CDS Source Code and CDS Object

In summary, I propose distinguishing **CDS objects** as runtime artifacts and **CDS source code** as design-time artifacts. The classification can be outlined as follows:

| **Source Code Type**                       | **Source Code Subtype**                   | **CDS Object**                           |
|--------------------------------------------|--------------------------------|------------------------------------------|
| **CDS Source Code**                        |   **CDS Source Code**                             | **CDS Object**                           |
| **Data Definition Language (DDL)**         |                                | **CDS Entity** (e.g., CDS View Entity, CDS Custom Entity, etc.) |
|                                            | **DDL Annotation (DDLA)**     | **CDS Annotation**                       |
|                                            | **DDL Metadata Extension (DDLX)** | **CDS Metadata Extension**               |
| **Data Control Language (DCL)**            |                                | **CDS Roles**                            |
| **Type Definition Language (TDL)**         |                                | **CDS User-Defined Types**               |
| **Function Definition Language (FDL)**     |                                | **CDS Function**                         |

I deliberately exclude **Service Definition Language (SDL)**, as it pertains to a different topic—the **RAP framework**. Nevertheless, it’s worth noting the close relationship between Service Definitions and the CDS framework.

Additionally, it’s important to highlight that the languages used for **annotations** and **metadata extensions** (**DDLA** and **DDLX**) are sub-dialects of the broader **DDL**.

## Syntactic Layer

In the **Syntactic Layer**, I am going to propose a classification of CDS entities based on their primary defining keyword. This approach organizes CDS artifacts according to the central syntax element that dictates their structure and functionality. By focusing on the main keyword, we can establish a clear and systematic understanding of the various CDS types.

### CDS by Keyword

**1. Syntax of ABAP CDS**<br>

1.1 **DEFINE ANNOTATION**<br>
1.2 **ANNOTATE VIEW**<br>
1.3 **ANNOTATE ENTITY**<br>

1.4 **DEFINE VIEW ENTITY**<br>

1.5 **DEFINE VIEW ENTITY AS PROJECTION ON**<br>
**Provide Contract: Transactional Query**<br>

1.6 **DEFINE VIEW ENTITY AS PROJECTION ON**<br>
**Provide Contract: Transactional Interface**<br>

1.7 **DEFINE TRANSIENT VIEW ENTITY AS PROJECTION ON**<br>
**Provide Contract: Analytical Query**<br>

1.8 **DEFINE VIEW**<br>
1.9 **DEFINE TABLE FUNCTION**<br>
1.10 **DEFINE HIERARCHY**<br>
1.11 **DEFINE CUSTOM ENTITY**<br>
1.12 **DEFINE ABSTRACT ENTITY**<br>
1.13 **DEFINE EXTERNAL ENTITY**<br>
1.14 **DEFINE VIEW ENTITY BUFFER**<br>

1.15 **DEFINE ROLE**<br>
1.16 **DEFINE ACCESS POLICY**<br>

1.17 **DEFINE TYPE**<br>
1.18 **DEFINE TYPE ENUM**<br>

1.19 **DEFINE SCALAR FUNCTION**<br>

1.20 **DEFINE ASPECT**<br>

2 **Extension Syntax**<br>

2.1 **EXTEND VIEW ENTITY**<br>
2.2 **EXTEND CUSTOM ENTITY**<br>
2.3 **EXTEND ABSTRACT ENTITY**<br>
2.4 **EXTEND VIEW**<br>

### Keyword Semantic

To express the semantics of the **CDS main keyword**, I have adopted a notation similar to **Backus-Naur Form (BNF)**, which is commonly used to describe the syntax of programming languages. In this approach, the **CDS main keyword** is constructed using the following components:

```EBNF
<keyword> ::= <cds_action> <cds_type>
<cds_action> ::= define | extend | annotate

<cds_type> ::= view | <entity> | <view_entity> | role | table_function | aspect | hierarchy | <type> | scalar_function | view_entity_buffer

<entity> ::= [custom | abstract | external] entity

<view_entity>  ::= [transient] view entity [as projection] [<contract>]

<contract> ::= provide contract transactional {query | interface} | analytical query

<type> ::= type | type enum
```

## Business Layer

The **Business Layer** represents the practical application of CDS as a modeling pillar, enabling the creation of business entities based on the technical foundation provided by the CDS framework. One of the key guides within this layer is the **Virtual Data Model (VDM)**, which standardizes the design and structure of CDS-based entities to align with business requirements.

VDM acts like a blueprint, similar to how Lego bricks can be assembled to build a castle. In this analogy, the Lego bricks represent the CDS framework components, while the final model—be it a **Remote API**, **Value Help**, or another business construct—symbolizes the resulting business entity. This approach ensures consistency, reusability, and alignment with SAP's overall architecture principles.

### VDM Type

The division of the **Business Layer** relies on the values of the **VDM.viewType** annotation. This annotation is a key component used by SAP for the internal structuring and interpretation of CDS views. It defines the purpose and role of each CDS view within the overall VDM architecture. Below are the specific types of VDM views:

1 **Basic CDS View**<br>

Represents the foundational layer of the VDM.
Typically maps to a single database table to provide raw data.
Used as a building block for higher-level CDS views.

2 **Composite CDS View**<br>

Combines multiple Basic CDS Views or other Composite Views.
Provides aggregated, enriched, or contextualized data.
Acts as a middle layer in the VDM hierarchy.

3 **Consumption CDS View**

Designed for use in user interfaces, analytics, or APIs.
Focuses on data presentation and consumption by external applications.
Often leverages SAP Fiori or analytical tools.

4 **Extension CDS View**

Used to extend existing CDS views without modifying the original definition.
Enables custom fields or logic to be added to standard SAP-delivered views.

5 **Derivation Function**

Facilitates the calculation of derived fields or values within a CDS view.
Often used for advanced calculations or dynamic data transformations.

6 **Transactional**

Supports transactional use cases.
Often associated with data modification or interactions in SAP’s transactional scenarios.

### CDS Purpose

**CDS Purpose Classification:**

1 **Views Providing Data Access**<br>

These views interact with the underlying database and are used for various data access purposes:

1.1 **Interface CDS View**<br>

Acts as an interface for data reading, often used as a source in Open SQL or as select source in other CDS views 

1.2 **Restricted Reuse CDS View**<br>

Provides entities with specific restrictions for usage outside of particular application area.
Restricted nature means that the CDS should not be used by customers or SAP partners in their developments. Don't confuse with Private CDS.

1.3 **Consumption CDS View**<br>

Focused on presenting data for analytics or user interfaces (e.g., SAP Fiori). Therefore they contain a plenty of consumption specific metadata. 

1.4 **Private CDS View**<br>

Intended for internal use as constituting part of other non-private CDS. Once it is created, it is used only in one specific place in CDS hierarchy.

1.5 **Transactional Processing CDS View**<br>

They are used for modelling CDS tree of business objects and enable capability of adding transactional behavior to them.

1.6 **Remote API CDS View**<br>

Exposes data as part of remote APIs for integration with external consumers. While Consumption CDS are created for specific consumption case providing a set consumption specific metadata, Remote API CDS are consumption and client agnostic reducing any redundant metadata.

1.7 **View Extends**<br>

Extends an existing CDS view to add additional fields or logic while keeping the original definition intact.

1.8 **View Extension Include**<br>

Created by key user extensibility supplier to enable this extension option for customers. To better understand this topic, I recommend exploring the **Key User Extensibility** documentation. Essentially, these views serve as anchors for further extensions views generated via key user apps

1.9 **Derivation Function**<br>

Performs derived field calculations within the CDS view.

2 **Views Without Data Access**<br>

These views do not directly access data but serve other modeling purposes:

2.1 **Abstract View**<br>

Provides an abstract structure used for ABAP typing and RAP action parameter modelling.


### CDS by Stability Contract

By stability contract:

1 **C0 Extend**<br>
These entities can be extended, with specific usage contexts:

1.1 **Use in Key User Apps**<br>
Designed for extensions via key user tools.

1.2 **Use in Cloud Development**<br>
Suitable for extensions in cloud-based development scenarios.

1.3 **Both context**<br>
Can be used in both key user apps and cloud development environments.

2 **C1 Use System-Internally**<br>
These entities are intended for internal system usage:

2.1 **Use in Key User Apps**<br>
Supports internal usage in key user scenarios.

2.2 **Use in Cloud Development**<br>
Designed for system-internal usage in cloud development.

3 **C2 Use as Remote API**<br>
These entities are exposed as remote APIs for external consumption.

### CDS by Lifecycle

By lifecycle status:

1 **Released**<br>
CDS views that are officially released for productive use. SAP and partner and customers shall utilize them in full grade.

2 **Deprecated**<br>
CDS views that are marked for future removal. While still available,  successor view is provided to substitute of deprecated one. Their usage is discouraged and all interesting actors have to adopt their code to replace with successor view.

3 **Decommissioned**<br>
CDS views that are no longer available or supported. The code adoption is completed. A particular time, usually defined by product owner, for notification of customers is over. They can be removed from the system at any time.

### CDS by Modelling Pattern

1 **None**<br>
Basic CDS views without any specific modeling pattern applied.

2 **Auxiliary Views**<br>
These views serve auxiliary purposes, such as supporting additional features or providing helper structures:

2.1 **Data Structure**: These entities are primarily used for parameter modeling in RAP actions or functions and for defining structured variable types in ABAP code. Typically, such CDS entities are not combined with other supported capabilities. Their exlusive purpose is to serve as data structures <br>

2.2 **Language Dependent**:These CDS entities provide translations or language-dependent texts. They are often based on text tables or table with domain values. Typically, they are linked to text consumer entities through associations.<br>

2.3 **Value Help Provider**: These CDS entities are used to supply value help for fields, such as dropdown lists or input assistance. They are typically based on database tables or existing CDS entities that contain the relevant value set. Value help providers are linked to consumer entities through associations and annotations, ensuring seamless integration with user interfaces.<br>

2.4 **Collective Value Help**: 
It refers to a CDS entity that combines multiple value help sources into a single, unified value help. This is useful when a field requires input assistance from different datasets or when the value help is context-specific.<br>

2.5 **Derivation Function**: 
It is a mechanism in SAP CDS views used to calculate or derive values dynamically based on specific business logic or conditions. These functions are often used to populate fields, restrict data, or enhance query results by deriving context-specific values, such as defaulting fiscal periods, calculating derived attributes, or mapping inputs to outputs. The CDS entity can be used as Derivation Function in an Consumption.derivation annotation.<br>

6 **Parent-Child Hierarchy Node Provider**<br>
Used for hierarchical data structures, enabling navigation between parent and child nodes. The CDS entity defines a parent-child hierarchy. Requests from the entity return hierarchy nodes with additional hierarchy-specific information, for example the size of the subhierarchy starting at a node. 
The entity can be used in hierarchy-navigation and hierarchy-aggregation functions.

7 **Enterprise Search Provider**<br>
These view entities are annotated with framework-specific **annotations EnterpriseSearch**. The annotations define search capabilities and they also trigger the generation of a **CDS-based search connector**. CDS-based enterprise search provides enhanced search capabilities in SAP Fiori launchpad.<br>

8 **RAP Framework**<br>
Focused on the SAP RESTful Application Programming model:

8.1 **Transactional Interface**: A CDS transactional interface is a CDS projection view that is intended to serve as **stable public interface for consumption**. A CDS transactional interface should be classified by a **release contract**(don't mixed up with provider contract) and thus serve as **released API**. They are typically used in the context of the ABAP RESTful Application Programming Model to provide the basis for a **RAP BO interface**. 
Technically, **BO interface layer** consists of a **CDS projection view** with the **provider contract transactional_interface** and a **Behavior Definition Interface** with implementation type **interface**.
A CDS transactional interface is defined using the CDS DDL statement **DEFINE VIEW ENTITY AS PROJECTION ON** and it must have its provider contract set to **TRANSACTIONAL_INTERFACE**. A CDS transactional interface is a CDS persistent entity.<br>

8.2 **Transactional Query**: A CDS projection view that is intended for modeling **transactional queries**. A transactional query is typically used in the context of the ABAP RESTful Application Programming Model to adapt a CDS data model **for service-specific use cases** (They are substitution of Consumption views). A transactional query is defined using the CDS DDL statement **DEFINE VIEW ENTITY AS PROJECTION ON** and it must have the provider contract set to **TRANSACTIONAL_QUERY**. A CDS transactional query is a CDS persistent entity.<br>

9 **Analytical Framework**<br>
Designed for analytics and reporting:

9.1 **Analytical Query**: Analytical queries are views that selects data from your analytical data model, based on specific use-cases requirements. Queries can also define the initial layout that is displayed in the output, and can be used to perform various analytical evaluations and calculations. They expose defined **measurement** and **dimensions**<br>

9.2 **Analytical Cube**: Data cube represents the multidimensional data model. All fields(except key fields) should be defined as **dimensions** or **measures**. The cube view is the center of a **Star/Snowflake schema** referencing dimension views (annotated with **Analytics.dataCategory: #DIMENSION**). CDS view as cube view has annotation **Analytics.dataCategory: #CUBE** in the header. A cube is the data source of an analytical query (analytical projection) and must contain **at least one measure**.<br>

9.3 **Analytical Dimension**: A dimension view provides extended information for combination of dimension and measure fields in Cube like **attributes**, **texts**, **hierarchies**. The view is annotated with **Analytics.dataCategory: #DIMENSION**
<br>

9.4 **Analytical Parent-Child Hierarchy Node**: The CDS entity can be used as a parent-child hierarchy in analytics. It is either an  analytical dimension, or connected to an analytical dimension. The rows of the entity represent nodes of the hierarchy. Currently only hierarchies defined by annotation Hierarchy.parentChild can be used in analytic models.<br>

9.5 **Analytical Document Store**: These CDS entities are usually annotated with: **objectModel.supportedCapabilities: #ANALYTICAL_DOCUMENT_STORE** and **objectModel.modellingPattern: #ANALYTICAL_DOCUMENT_STORE**.
Also, they have a specific data category: **Analytics.dataCategory: #DOCSTORE**.
Moreover, these CDS entities should be linked with the parent CDS Analytics Cube via the annotation **Analytics.document.storageForEntity: ['Name_of_Cube']**.
And last but not least, the annotation **Analytics.document.serviceClassName: '<IF_RSDOC_SERVICE_VIR>'** should be placed in the CDS header.
A CDS-based Document Store handles Document IDs and their assignment to cells in a query result. The actual documents are handled by the application. To achieve this, the application must implement a class that implements a special interface IF_RSDOC_SERVICE_VIRT, and the name of this class must be assigned to the Document CDS view.<br> 

9.6 **Analytical Fact**: Facts are an **optional** part of an analytical data model in ABAP analytics. A fact can be used as a **data source for a cube**. The fact view has annotation **Analytics.dataCategory: #FACT** in the header<br>

9.7 **Analytical KPI**:The Analytical KPI CDS is designed to represent Key Performance Indicators (KPIs) within SAP's analytical frameworks. KPIs provide measurable values that help organizations assess the performance of their processes, operations, or objectives.<br>

10 **Output Management**<br>
Enables data preparation for outputs like forms and emails:

10.1 **Output Form Data Provider**: Supplies data for forms.<br>

10.2 **Output Email Data Provider**: Provides data for email templates.<br>

10.3 **Output Parameter Determination Data Source**: Helps in determining parameters for output processes.<br>

11 **Situation Framework**<br>
Handles contextual situations and notifications:

11.1 **Situation Anchor**: Defines the primary anchor bussines object for a situation.<br>

11.2 **Situation Trigger**: Specifies the events or triggers for a situation.<br>

11.3 **Situation Data Context**: Provides the data context for evaluating situations.<br>

12 **External Data Provider**<br>
Integrates data from external sources into the CDS framework. I suppose that pattern is imposed exactly for CDS External Entities.

It's worth mentioning that for hierarchy modeling, we can also distinguish patterns such as **hierarchy source CDS** and **CDS hierarchy directory**. 
Moreover, CDS hierarchies can be modeled in a **time-dependent** or **permanent** manner.

Regarding points 10–11, they remain unfamiliar territory to me. Therefore, I would greatly appreciate it if you, dear reader, could share a detailed guide on them. Thank you in advance!
