# BigQuery Remote MCP Extension for Gemini CLI

> **Preview:** This product is subject to the "Pre-GA Offerings Terms" in the General Service Terms section of the [Service Specific Terms](https://docs.cloud.google.com/terms/service-terms#1). Pre-GA products and features are available "as is" and might have limited support. For more information, see the [launch stage descriptions](https://cloud.google.com/products#product-launch-stages).

The BigQuery extension for Gemini CLI enables you to interact with Google BigQuery using natural language commands. This makes it easier to query data, manage datasets, and perform other BigQuery operations directly through Gemini CLI.

## Why use the BigQuery remote MCP server?

Google and Google Cloud remote MCP servers can be used in your AI applications with enterprise-ready governance, security, and access control through our [remote MCP servers](https://docs.cloud.google.com/mcp/overview).

## Before you begin

1. In the Google Cloud console, on the [project selector page](https://console.cloud.google.com/projectselector2/home/dashboard), select or create a Google Cloud project.  

   > **Note**: If you don't plan to keep the resources that you create in this procedure, create a project instead of selecting an existing project. After you finish these steps, you can delete the project, removing all resources associated with the project.  

2. Get your administrator to grant you the [MCP Tool User role](https://docs.cloud.google.com/iam/docs/roles-permissions/mcp#mcp.toolUser) (`roles/mcp.toolUser`) on the Google Cloud project. If you created a new project, then you already have the required permissions.
3. Ensure your administrator has enabled the [BigQuery API](https://console.cloud.google.com/marketplace/product/google/bigquery.googleapis.com) on the Google Cloud project.

## Configure authentication

This extension uses Google Application Default Credentials (ADC) to perform authentication. To login with ADC, run the following command in your terminal:

```bash
gcloud auth application-default login
```

For additional details, see the [ADC documentation](https://docs.cloud.google.com/docs/authentication/application-default-credentials#personal).

## Install the extension

To install the extension, run the following command in your terminal:

```bash
gemini extensions install https://github.com/GoogleCloudPlatform/bigquery-remote-mcp
```

## Available tools

To see a complete list of available tools and their schemas, see the [BigQuery MCP reference](https://docs.cloud.google.com/bigquery/docs/reference/mcp).

## Limitations

The BigQuery MCP tools are subject to the following limitations:

- The execute_sql tool doesn't support querying Google Drive external tables.
- By default, the execute_sql tool limits query processing time to three minutes. Queries that run longer than three minutes are automatically canceled.
- Query results are limited to a maximum of 3,000 rows.

## Sample use cases

The following are sample use cases for the BigQuery MCP server:

- Build workflows that use insights from BigQuery data to trigger certain actions such as creating issues and composing emails.
- Use BigQuery's advanced capabilities like forecasting for higher-order insights.
- Build a conversational experience for your users with custom agent instructions.

### Sample prompts

You can use the following sample prompts to get information about BigQuery resources, gain insights, and analyze BigQuery data:

- List the datasets in project `PROJECT_ID`.
- Find all the queries that I ran in project `PROJECT_ID` using the MCP server in the `REGION` region. Use the tag goog-mcp-server:true to identify the query jobs that ran through the MCP server.
- Find the top orders by volume from `DATASET_ID` in project `PROJECT_ID`. Identify the appropriate tables, find the correct schema, and show the results.
- Create a forecast on the table `PROJECT_ID.DATASET_ID.TABLE_ID` for future years. Use `COLUMN_NAME` as the data column and `COLUMN_NAME` as the timestamp column. Show the top 10 forecasts.

In the prompts, replace the following:

- `PROJECT_ID`: the Google Cloud project ID
- `REGION`: the name of the region
- `DATASET_ID`: the name of the dataset
- `TABLE_ID`: the name of the table
- `COLUMN_NAME`: the name of the column

## Optional security and safety configurations

MCP introduces new security risks and considerations due to the wide variety of actions that you can take with MCP tools. To minimize and manage these risks, Google Cloud offers defaults and customizable policies to control the use of MCP tools in your Google Cloud organization or project.

For more information about MCP security and governance, see [AI security and safety](https://docs.cloud.google.com/mcp/ai-security-safety).

## Quotas and limits

The BigQuery MCP server doesn't have its own quotas. There is no limit on the number of call that can be made to the MCP server. You are still subject to the quotas enforced by the APIs called by the MCP server tools.

## Reference and resources

* Explore the [BigQuery remote MCP server reference documentation](https://docs.cloud.google.com/bigquery/docs/reference/mcp), which includes a list of all available tools, and the full input and output schema for each tool.  
* See the [BigQuery overview](https://cloud.google.com/bigquery).
* Learn about [MCP security and governance](https://docs.cloud.google.com/mcp/ai-security-safety).
