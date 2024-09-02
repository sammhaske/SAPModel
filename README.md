# SAP Model – Dynamic table version

[Version Information](#_version_information)

[Introduction](#_introduction)

[Overview of the SAP Model](#_overview_of_SAP_model)

[Scope](#_scope)

[Data Source](#_data_source)

[High\-level Architecture Diagram](#_architecture_diagram)

[Detailed Model Description](#_detail_model_decription)

## <a id="_Toc850193016"></a><a id="_version_information"></a>Version Information

Model Name:  SAP Model – Dynamic Table Version

Project Name:

Branch Name:

Documentation Version: 1\.0

Current Version: 1\.0

Originally Developed by: Shubham Mhaske

Materialization Type: Dynamic Tables

## <a id="_Toc112519443"></a><a id="_introduction"></a>Introduction:

__This documentation provides a comprehensive overview of the SAP extractor models created using Coalesce\. The primary objective of these models is to facilitate a deeper understanding of SAP data by recreating essential extractor models and bringing in critical master and transactional data into a unified environment\.__

__The package covers key aspects of SAP data management, including the extraction of master attribute tables, general ledger models, and master text tables\. By doing so, it ensures that all vital components of the SAP landscape are accessible for analysis and reporting\.__

__This document is intended for technical users, who need to interact with or maintain this SAP model\. It provides detailed insights into the architecture, design, and implementation of the models, along with instructions for usage, troubleshooting, and version control\.__

## <a id="_overview_of_SAP_model"></a><a id="_Toc1953365171"></a>Overview of the SAP Model:

This package provides recreations of SAP extractor models to help you gain a deeper understanding of your SAP data\. It accomplishes this by:

•	Importing key master attribute tables such as Company Code \(sap\_\_0comp\_code\_attr\), Customer Master \(sap\_\_0customer\_attr\), Employee \(sap\_\_0employee\_attr\), G/L Account Number \(sap\_\_0gl\_account\_attr\), Material Data \(sap\_\_0material\_attr\), and Vendor Number \(sap\_\_0vendor\_attr\)\.

•	Including general ledger models like General Ledger: Balances, Leading Ledger \(sap\_\_0fi\_gl\_10\), and Line Items Leading Ledger \(sap\_\_0fi\_gl\_14\)\.

•	Incorporating master text models such as Company Code \(sap\_\_0comp\_code\_text\), Company \(sap\_\_0company\_text\), and Vendor \(sap\_\_0vendor\_text\)\.

## <a id="_scope"></a><a id="_Toc1445996240"></a>Scope:

The following table provides a detailed list of all models materialized within this package by default\.


| Model                                  | Description                                                                                    |
| -------------------------------------- | ---------------------------------------------------------------------------------------------- |
| DT\_DIM\_SAP\_\_0COMP\_CODE\_ATTR      | This model is used for loading company code attributes, extracting from the t001 data source\.       |
| DT\_DIM\_SAP\_\_0COMP\_CODE\_TEXT      | This model is used for loading company code text information, extracting from the t001 data source\. |
| DT\_DIM\_SAP\_\_0COMPANY\_TEXT         | This model is used for loading customer text data, extracting from the t880 data source\.            |
| DT\_DIM\_SAP\_\_0CUSTOMER\_ATTR        | This model is used for loading customer master data, originating from the kna1 source\.              |
| DT\_DIM\_SAP\_\_0EMPLOYEE\_ATTR        | This model contains information that concerns the employee's work relationship, extracting master data from the personnel administration tables\.       |
| FACT\_SAP\_\_0FI\_GL\_10               | This model extracts the transaction figures from the leading ledger in the new General Ledger\.      |
| DT\_WRK\_SAP\_\_0FI\_GL\_14            | This model extracts line items from the leading ledger in the new General Ledger Accounting\.       |
| DT\_DIM\_SAP\_\_0GL\_ACCOUNT\_ATTR     | This model is used for loading G/L Account Number master data, originating from the ska1 source\. |
| DT\_DIM\_SAP\_\_0MATERIAL\_ATTR        | This model is used to display material attribute information, originating from the mara source\.       |
| DT\_DIM\_SAP\_\_0VENDOR\_ATTR          | This model is used to display vendor attributes, originating from the lfa1 source\. |
| DT\_DIM\_SAP\_\_0VENDOR\_TEXT          | This model is used to display vendor text, originating from the lfa1 source\.       |


## <a id="_data_source"></a><a id="_Toc1308288373"></a>Data Source:

The following source tables are integral to the SAP model\. These tables provide the foundational data required for accurate extraction, transformation, and reporting within the system\. Below is a list of the key source tables, each with a brief description of its purpose and role in the model:

| Sources                                  | Description                                                                   |
| ---------- | ---------------------------------------------------------------------------------------------- |
| BKPF       | Stores header information for accounting documents, including document type, date, and company code\. |
| BSEG       | Contains detailed line items for accounting documents, such as account numbers, amounts, and tax data\. |
| FAGLFLEXA  | Records line items in the general ledger, supporting detailed financial analysis and reporting\.            |
| FAGLFLEXT  | Stores summarized financial totals in the general ledger for aggregate reporting\.             |
| KNA1       | Holds general customer data, essential for managing customer relationships and sales processes\.       |
| LFA1       | Contains general data on vendors, supporting procurement and supplier management\.      |
| MARA       | Stores comprehensive information about materials, critical for inventory management and production\.      |
| PA0000     | Contains core HR data, including organizational assignments and employee information\. |
| PA0001     | Records employees’ organizational assignments, crucial for HR management and payroll\.       |
| PA0007     | Stores data on employees planned working hours, used for time management and payroll\. |
| PA0008     | H Contains information on employees’ basic pay, key for payroll processing\.      |
| PA0031     | Records data on employees’ participation in company pension schemes\. |
| SKA1       | Stores master data for G/L accounts, forming the basis for financial accounting and reporting\. |
| T001       | Contains data on company codes, which represent independent accounting entities within the organization\. |
| T503       | Holds classification data for employee groups, used in HR processes\. |
| T880       | Stores global company code information, used for financial consolidation across multiple entities\.|


## <a id="_architecture_diagram"></a><a id="_Toc1464342256"></a>High\-level architecture diagram:

{{put your image}}

## <a id="_detail_model_decription"></a><a id="_Toc384784864"></a>Detailed Model Description:

**1. DT\_DIM\_SAP\_\_0COMP\_CODE\_ATTR:**

This model is used for loading company code attributes, extracting from the t001 	data source\.

Source Table:

- Name: T001
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0COMP\_CODE\_ATTR
- Materialization: Dynamic Table

{{put your image}}

**2. DT\_DIM\_SAP\_\_0COMP\_CODE\_TEXT**

This model is used for loading company code text information, extracting from the 	t001 data source\.

Source Table:

- Name: T001
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0COMP\_CODE\_TEXT
- Materialization: Dynamic Table

{{put your image}}

**3. DT\_DIM\_SAP\_\_0COMPANY\_TEXT**

This model is used for loading customer text data, extracting from the t880 data 	source\.

Source Table:

- Name: T880
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0COMPANY\_TEXT
- Materialization: Dynamic Table

{{put your image}}

**4. DT\_DIM\_SAP\_\_0CUSTOMER\_ATTR**

This model is used for loading customer master data, originating from the kna1 	source\.

Source Table:

- Name: KNA1
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0CUSTOMER\_ATTR
- Materialization: Dynamic Table

{{put your image}}

**5. DT\_DIM\_SAP\_\_0EMPLOYEE\_ATTR**

This model contains information that concerns the employee's work relationship, 	extracting master data from the personnel administration tables\.

Source Table:

- Name: PA0000, PA0001, PA0007, PA0008, PA0031, T503
- Materialization: Source

Intermediate Tables:

- Name: DT\_WRK\_INT\_SAP\_\_0EMPLOYEE\_DATE\_CHANGES, 		 	DT\_WRK\_INT\_SAP\_\_0EMPLOYEE\_DATE\_CHANGES\_1, 				DT\_WRK\_INT\_SAP\_\_0EMPLOYEE\_DATE\_CHANGES\_2, 				DT\_WRK\_INT\_SAP\_\_0EMPLOYEE\_DATE\_CHANGES\_3
- Materialization: Dynamic Tables Work

Target Table:

- Name: DT\_DIM\_SAP\_\_0EMPLOYEE\_ATTR
- Materialization: Dynamic Table Dimension

{{put your image}}

**6. FACT\_SAP\_\_0FI\_GL\_10**

This model extracts the transaction figures from the leading ledger in the new 			General Ledger\.

Source Table:

- Name: FAGLFLEXT, T001
- Materialization: Source

Intermediate Tables:

Name: V\_STG\_INT\_SAP\_\_0FI\_GL\_10\_SUMS,			             	V\_INT\_SAP\_\_0FI\_GL\_10\_UNPIVOT

- Materialization: View

Target Table:

- Name: FACT\_SAP\_\_0FI\_GL\_10
- Materialization: Fact Table

{{put your image}}

**7. DT\_WRK\_SAP\_\_0FI\_GL\_14**

This model extracts line items from the leading ledger in the new General Ledger 	Accounting\.

Source Table:

- Name: BKPF, FAGLFLEXA, BSEG
- Materialization: Source

Target Table:

- Name: DT\_WRK\_SAP\_\_0FI\_GL\_14
- Materialization: Dynamic Table

{{put your image}}

**8. DT\_DIM\_SAP\_\_0GL\_ACCOUNT\_ATTR**

This model is used for loading G/L Account Number master data, originating from the 	ska1 source\.

Source Table:

- Name: SKA1
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0GL\_ACCOUNT\_ATTR
- Materialization: Dynamic Table

{{put your image}}

**9. DT\_DIM\_SAP\_\_0MATERIAL\_ATTR**

This model is used to display material attribute information, originating from the mara 	source\.

Source Table:

- Name: MARA
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0MATERIAL\_ATTR
- Materialization: Dynamic Table

{{put your image}}

**10. DT\_DIM\_SAP\_\_0VENDOR\_ATTR**

This model is used to display vendor attributes, originating from the lfa1 source\.

Source Table:

- Name: LFA1
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0VENDOR\_ATTR
- Materialization: Dynamic Table

{{put your image}}

**11. DT\_DIM\_SAP\_\_0VENDOR\_TEXT**

This model is used to display vendor text, originating from the lfa1 source\.

Source Table:

- Name: LFA1
- Materialization: Source

Target Table:

- Name: DT\_DIM\_SAP\_\_0VENDOR\_TEXT
- Materialization: Dynamic Table

{{put your image}}

