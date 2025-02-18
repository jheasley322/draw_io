:::mermaid
graph TD
    %% Define Core Systems
    subgraph "Core Systems"
        oracle_erp["Oracle ERP"]
        blue_yonder["Blue Yonder"]
        workday["Workday"]
        jira["Jira"]
        confluence["Confluence"]
        azure_storage["Azure Storage"]
        onedrive_sharepoint["OneDrive/SharePoint"]
    end

    %% Data Warehouse
    subgraph "Data Warehouse"
        databricks["Databricks Warhouse"]
        databricks_dm["Databricks Data Mart"]
    end

    %% Qlik Ecosystem
    subgraph "Qlik Ecosystem"
        qdi_replicate["QDI - Replicate (CDC & Data Movement)"]
        qdi_transform["QDI - Transformation & Modeling"]
        user_managed_data["User Managed Data"]
        qlik_catalog["Qlik Catalog"]

        subgraph "Qlik Sense (Analytics Hub)"
            analytics_apps["Analytics Apps"]
            report_distribution["Report Distribution"]
            ml_model["ML Model"]
            ai_assist["AI Assistance"]
            notifications["Notifications"]
            ad_hoc_ua["Ad-Hoc User Analysis"]
        end
    end

    %% Data Movement
    oracle_erp --> qdi_replicate
    blue_yonder --> qdi_replicate
    workday --> qdi_replicate
    jira --> qdi_replicate
    confluence --> qdi_replicate
    azure_storage --> qdi_replicate
    onedrive_sharepoint --> qdi_replicate
    onedrive_sharepoint --> user_managed_data
    user_managed_data --> qdi_transform

    %% QDI Moving Data
    qdi_replicate --> databricks
    databricks --> qdi_transform
    qdi_transform --> databricks_dm


    %% Qlik Sense Consumption
    user_managed_data --> ad_hoc_ua
    qlik_catalog --> databricks_dm
    qlik_catalog --> analytics_apps
    qlik_catalog --> report_distribution
    qlik_catalog --> ml_model
    qlik_catalog --> ai_assist
    qlik_catalog --> notifications
    user_managed_data --> qlik_catalog