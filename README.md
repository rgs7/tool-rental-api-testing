# Tool Rental API - Postman Collection

This Postman collection allows interaction with the Tool Rental API. It includes requests to check API status, retrieve available tools, create orders, and manage them.

## Features
- Check API status.
- Retrieve available tools.
- Create, update, and delete orders.
- Use variables to facilitate test execution.
- Automated workflow using response-generated variables.

## Setup
1. Import the `Tool_Rental.postman_collection.json` collection into Postman.
2. Define the following environment variables:
   - `baseUrl`: `https://simple-tool-rental-api.glitch.me`
   - `token`: Authentication token (generated upon registering an API client).
   - `category`: Tool category to filter.
3. Ensure that `baseUrl` and `token` are correctly set before executing protected requests.

## Execution Flow
This collection is designed to run as an automated workflow, where responses from certain requests set variables for subsequent ones. Example:
1. **Get all tools** (`Get all tools`) stores `toolId`.
2. **Get a single tool** (`Get a single tool`) validates `toolId` and moves to the next request.
3. **Create a new order** (`Create a new order`) uses `toolId` and generates `orderId`.
4. **Verify created order** (`Get a single order`) confirms `orderId`.
5. **Delete an order** (`Delete an order`) removes the created order.
6. **Verify deletion** (`Verify deleted order`) confirms the order no longer exists.

## Run the Collection with Postman
To run all requests sequentially:
1. Open the collection in Postman.
2. Click the `Run` button in the collection section.
3. Select the correct environment with configured variables.
4. Execute the collection and check results in the `Test Results` tab.

## Run the Collection with Newman
To execute the collection via command line using [Newman](https://www.npmjs.com/package/newman):

1. Open a terminal.
2. Navigate to the directory containing the Postman collection JSON file.
3. Run the following command:
   ```sh
   newman run Tool_Rental.postman_collection.json
   ```

## Additional Notes
- Some requests require authentication via a `token`. Generate one by registering a new API client.
- Globally stored variables facilitate workflow execution without manual intervention.
- If any request fails, check the variable values and adjust if necessary.

