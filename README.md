
# Teradata MCP Server Template

This code will form the basis for building Teradata MCP servers.


### Environment Set Up
Step 1 - The environment has been put together assuming you have the uv package installed on your local machine.  Installation instructions for uv can be found at https://github.com/astral-sh/uv 

Step 2 - Clone the mcp-server repository with 

```
mkdir MCP
cd MCP
git clone https://github.com/Teradata/mcp-server.git
cd mcp-server
uv sync
source .venv/bin/activate
```


Step 3 - You need to update the .env file
- Rename env file to .env 
- The database URI will have the following format  teradata:/username:password@host:1025/databasename, use a ClearScape Analytics Experience https://www.teradata.com/getting-started/demos/clearscape-analytics
    - the usename needs updating
    - the password needs updating
    - the Teradata host needs updating
    - the databasename needs updating

- LLM Credentials need to be available for pydantic-ai-example.ipynb code to work

### Testing your server
Step 1 - Start the server, typer the following in your terminal
```
mcp dev ./teradata_mcp/src/server.py
```

Step 2 - Open the MCP Inspector
- You should open the inspector tool, go to http://127.0.0.1:6274 
- Click on tools
- Click on list tools
- Click on list_db
- Click on run

Test the other three tools, each should have a successful outcome

Control+c to stop the server in the terminal

### Adding your sever to an Agent
Step 1 - run the test script, this will create an interactive session with the agent who has access to the MCP server.  

From a terminal.
```
cd mcp-server
python test/pydanticai.py
```

- Ask the agent to list the databases
- Ask the agent to list the table in a database
- Ask the agent to show all the objects in a database
- Ask the agent a question that requires SQL to run against a table
- This is running in a loop, you will need to Control-C to break the loop.
