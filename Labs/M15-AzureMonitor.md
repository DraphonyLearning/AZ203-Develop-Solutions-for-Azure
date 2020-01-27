# Azure Monitors


## Objectives
In this lab, we will:
1. Use the HTTP Data Collector API from Azure to add log items into a Log Analytics Workspace.


## Instructions
### Setup up your development environment & Azure
* Download & Install [.NET Core SDK](https://dotnet.microsoft.com/download)
* Download & Install [Visual Studio Code](https://code.visualstudio.com/)
* Or Download & Install [Visual Studio](https://visualstudio.microsoft.com/)
* Activate your [Azure Pass](https://www.microsoftazurepass.com/)

### Setup your Azure Resources
* Go to Azure [Portal](https://portal.azure.com)
* Create a new Log Analytics Workspace and wait until the deployment is done.
* Open the Log Analytics Workspace and open the Sub-Blade "Advanced Settings", note down the first Key.

### Develop solutions
* Create a new solution using .NET Core CLI
    ```bash
    mkdir AzureMonitor
    dotnet new console --output ./AzureMonitor --name AzureMonitor
    cd AzureMonitor
    dotnet restore
    code .
    ```
* Use the [System.Net.Http.HttpClient](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient?view=netcore-3.1) to send POST request to your Workspace
* Check Azure Monitor, that your requests has been added.
  (**It may takes a few minutes until your data are shown in the Azure Monitor blade**)

#### Hints
* [Azure Log Analytics HTTP Data Collector API](https://docs.microsoft.com/en-us/rest/api/loganalytics/create-request)
* [StringContent](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.stringcontent?view=netcore-3.1)
* [Convert.FromBase64String](https://docs.microsoft.com/en-us/dotnet/api/system.convert.frombase64string?view=netcore-3.1)
* [System.Security.Cryptography.HMACSHA256](https://docs.microsoft.com/en-us/dotnet/api/system.security.cryptography.hmacsha256?view=netcore-3.1)

