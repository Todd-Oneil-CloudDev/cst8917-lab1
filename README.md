# Serverless Lab1
## Author: Todd O'Neil

### Demo:
[Link to Demo](https://www.youtube.com/watch?v=PN9IcBxbyvw)

### Requirements:
This project requires the following:
- CosmosDB instance
- python 3.12 or higher

### Instructions:
#### Step 1:
Clone this repository.

#### Step 2:
Create a local.settings.json file and populate it with the following variables:
```
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "DATABASE_NAME": "<your cosmosdb name>",
    "DATABASE_COLLECTION": "<your cosmosdb container>",
    "DATABASE_KEY": "<your cosmos primary key>",
    "DATABASE_CONNECTION_STRING": "<your cosmos uri>"
  }
}
```

#### Step 3:
Create a virtual environment and activate it using the following commands:
``` bash
python -m venv venv
source venv/bin/activate
```

#### Step 4:
Install all dependencies from requirements.txt with
```bash
pip install -r requirements.txt
```

#### Step 5:
Start the function with
```bash
func start
```

#### Step 6:
You should now be able to access each endpoint.  
To use '/api/TextAnalyzer' endpoint there are 2 approaches.
- using curl
    - curl "http://localhost:7071/api/TextAnalyzer?text=Serverless%20computing%20is%20amazing.%20It%20scales%20automatically."
- using the browser
    - http://localhost:7071/api/TextAnalyzer?text=Serverless%20computing%20is%20amazing.%20It%20scales%20automatically.

To use '/api/GetAnalysisHistory' there is also 2 approaches.  
- using curl
    - curl "http://localhost:7071/api/GetAnalysisHistory"
- using the browser
    - http://localhost:7071/api/GetAnalysisHistory

'/api/GetAnalysisHistory' also has an optional parameter to set a limit to the number of returned results. Adding ?limit=[number] at the end of the path will limit the number of results i.e. http://localhost:7071/api/GetAnalysisHistory?limit3 will only return 3 results.