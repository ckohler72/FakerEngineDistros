<!-- @format -->

# FakerEngine - User Guide

Welcome to FakerEngine! This guide will help you get started with generating fake data, testing APIs, and seeding databases.

## What is FakerEngine?

FakerEngine is a desktop application that helps you:

- Generate realistic fake data for testing and development
- Test APIs by sending data to endpoints
- Seed databases with generated data
- Automate complex workflows combining API calls and database operations

## Quick Start

### 1. First Steps

![Dashboard](ScreenShots/Dashboard.jpg)

1. **Launch the application** - Double-click the FakerEngine icon
2. **Start on the Dashboard** - View your statistics and recent activity
3. **Create a Data Structure** - Go to **Data Structures** to define what kind of data you want to generate

### 2. Create Your First Data Structure

![Data Structures List](ScreenShots/DataStructures-List.jpg)

1. Navigate to **Data Structures** → **Data Structures**
2. Click **"Create Structure"**
3. Add fields and choose their types:
   - **Basic Types**: string, number, boolean, date, email, phone, address, etc.
   - **JSON**: Create JSON objects (static or dynamic with nested fields)
   - **Arrays**: Generate lists of values
   - **Objects**: Create nested data structures
4. Click **"Save Structure"**

![Data Structures Edit](ScreenShots/DataStructures-Edit.jpg)

### 3. Preview Your Data

![Preview Data](ScreenShots/PreviewData.jpg)

1. Go to **Data Structures** → **Preview Data**
2. Select your structure
3. Choose how many records to generate
4. Click **"Generate Data"** to see the results

## Key Features

### Data Structures

Create reusable data structures with various field types:

- **String**: Random text
- **Number**: Random integers (with min/max)
- **Email, Phone, Address**: Realistic contact information
- **Static**: Same value for all records
- **JSON**: Static JSON strings or dynamic JSON with nested fields
- **Array**: Lists of values
- **Object**: Nested data structures

### Endpoints & API Testing

1. **Configure Platforms & Environments**

![Environments](ScreenShots/Environments.jpg)

- Go to **Environments** → **Platforms** to create platforms
- Go to **Environments** → **Environments** to set up environment variables

2. **Create Endpoints**

![Endpoints List](ScreenShots/Endpoints-List.jpg)

- Navigate to **Endpoints** → **Endpoints**
- Add endpoint URL, method (GET/POST/PUT/PATCH/DELETE)
- Configure authentication (Bearer Token, Basic Auth, API Key)
- Add headers, query parameters, and request body

![Endpoints Edit](ScreenShots/Endpoints-Edit.jpg)

3. **Send Data**

![Send Data](ScreenShots/SendData.jpg)

- Go to **Endpoints** → **Send Data**
- Select endpoint and data structure
- Choose count and environment
- Click **"Send Data"** to test your API

### Database Seeding

1. **Set Up Database Connection**

![Connections](ScreenShots/Connections.jpg)

- Go to **Database Management** → **Connections**
- Add connection for MySQL, PostgreSQL, or MongoDB
- Test the connection

2. **Create a Seeder**

![Seeders](ScreenShots/Seeders.jpg)

- Navigate to **Database Management** → **Seeder**
- Click **"New Seeder"**
- Select connection, database, and table
- Choose data structure and map fields to columns
- Set record count and save

3. **Execute Seeder**
   - Click **"Execute"** on a saved seeder
   - View results with inserted record counts

### Seeder Runs

![Seeder Runs](ScreenShots/SeederRuns.jpg)

Create sequential database seeding workflows:

1. Go to **Database Management** → **Seeder Runs**
2. Click **"New Seeder Run"**
3. Add multiple seeder steps
4. Use data from previous steps with `{{previous.field}}` or `{{stepN.field}}`
5. Configure delays between steps
6. Execute the complete workflow

### Simulations

![Simulations List](ScreenShots/Simulations-List.jpg)

Create multi-step API testing workflows:

1. Navigate to **Endpoints** → **Simulations**
2. Create a new simulation
3. Add steps with endpoints to call
4. Use data from previous steps in subsequent steps
5. Execute manually or schedule as a job

![Simulations Edit](ScreenShots/Simulations-Edit.jpg)

### Workflows

![Workflows List](ScreenShots/Workflows-List.jpg)

Combine API calls and database operations:

1. Go to **Dashboard** → **Workflows** (or **Endpoints** → **Workflows**)
2. Create a new workflow
3. Add steps:
   - **Simulations**: Execute API calls
   - **Seeder Runs**: Perform database operations
4. Configure delays and step ordering
5. Execute complete workflows

![Workflow Edit](ScreenShots/WorkFlow-Edit.jpg)

### Schedules

![Schedules List](ScreenShots/Schedules-List.jpg)

Automate repetitive tasks:

1. Go to **Endpoints** → **Schedules**
2. Create a schedule for an endpoint or simulation
3. Configure:
   - Interval (seconds, minutes, hours)
   - Requests per interval
   - Total requests
4. Start the schedule and monitor progress

![Schedules Edit](ScreenShots/Schedules-Edit.jpg)

### Viewing History & Logs

![Send History](ScreenShots/SendHistory.jpg)

- **Send History**: **Endpoints** → **Send History** - View all API requests/responses

![Send History Details](ScreenShots/SendHistory-Details.jpg)

- **Seeder Log**: **Database Management** → **Seeder Log** - Review database seeding executions

![Seeder Logs](ScreenShots/SeederLogs.jpg)

- **Workflow Log**: **Endpoints** → **Workflow Log** - Track workflow execution history

All logs include:

- Success/failure status
- Duration and timing
- Detailed results
- Error messages (if any)

## Using Context Variables

### In Simulations

- `{{previous.field}}` - Use data from the previous step
- `{{step1.field}}` - Use data from step 1 (or any step number)
- `{{env.VARIABLE_NAME}}` - Use environment variable

### In Seeder Runs

- `{{previous.field}}` - Use data from the previous seeder step
- `{{step1.field}}` - Use data from step 1
- Works with inserted record IDs and data

### In Workflows

- Workflows can combine simulations and seeder runs
- Context flows between steps automatically

## Tips & Best Practices

1. **Start Simple**: Create basic data structures first, then add complexity
2. **Save Everything**: Save your structures, seeders, and workflows for reuse
3. **Use Environments**: Set up different environments for dev/staging/production
4. **Test Connections**: Always test database connections before seeding
5. **Preview Data**: Use Preview Data to verify structures before using them
6. **Check Logs**: Review execution logs to troubleshoot issues
7. **Export Data**: Use Export/Import to backup your configurations

## Troubleshooting

### Backend Connection Issues

- Ensure the application has network permissions
- Check if port 38765 is available
- Restart the application if needed

### Database Connection Fails

- Verify database server is running
- Check connection credentials
- Ensure firewall allows connections
- Test connection using the "Test Connection" button

### Seeding Errors

- Verify field mappings match database columns
- Check data types are compatible
- Ensure required fields are mapped
- Review error messages in Seeder Log

### API Requests Fail

- Verify endpoint URL is correct
- Check authentication credentials
- Review headers and request body format
- Check Send History for detailed error messages

### Data Not Generating

- Verify structure has at least one field
- Check field configurations are valid
- Use Preview Data to test structures
- Review console for error messages

## Data Storage

Your data is stored locally on your computer:

- **macOS**: `~/Library/Application Support/FakerEngine/data/`
- **Windows**: `%APPDATA%/FakerEngine/data/`
- **Linux**: `~/.config/FakerEngine/data/`

You can backup your data using **System Administration** → **Export / Import**.

## Support

For issues, questions, or feature requests:

- Check the application logs
- Review the execution history and logs
- Export your configuration for troubleshooting

## Version

Current version: **2.0.0**

---

**Enjoy using FakerEngine!** 🚀
