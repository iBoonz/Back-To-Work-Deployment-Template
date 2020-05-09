# Send Proactive messages to the Healthbot via an Azure function

This repository contains an Azure Function that will trigger a Microsoft Healhtbot service scenario.

There is also an ARM template that can be executed to deploy the Function in your Azure tenant.

## Prerequisites

This Function requires an Azure API for FHIR server, the following [Github](https://github.com/iBoonz/fhir-server-self-observation) repository explains how to deploy a FHIR server, with the required Service Principal (Client)

Before deploying the samples scenario make sure that you have Az and AzureAd powershell modules installed:

Install-Module Az
 

## Deployment

To deploy the sample scenario, first clone this git repo and find the deployment scripts folder:

git clone https://github.com/iBoonz/https://github.com/iBoonz/Back-to-Work-Trigger
cd Back-to-Work-Trigger/deploy

Log into your Azure subscription:
Login-AzAccount

Then deploy the function with the Powershell or Bash script:
.\azureDeploy.ps1

The template requires the following parameters.
You can fill these in the parameters JSON file, found in the ARM templates folder

```
"Healthbot_Trigger_Uri": {
        "type": "securestring",
        "metadata": {
            "description": "the Healthbot URI to trigger the scenario"
        }
    },
"Healthbot_API_JWT_SECRET": {
        "type": "securestring",
        "metadata": {
            "description": "The API JWT from the Healthbot"
        }
    },
"Healthbot_Name": {
        "type": "securestring",
        "metadata": {
            "description": "The name of the healthbot"
        }
    },
"Healthbot_ScenarioId": {
        "type": "securestring",
        "metadata": {
            "description": "The name of the scenario that will be triggered"
        }
    },
"FHIR_Audience": {
        "type": "securestring",
        "metadata": {
            "description": "The FHIR audience URI"
        }
    },
"FHIR_Authority": {
        "type": "securestring",
        "metadata": {
            "description": "The FHIR authority URI"
        }
    },
"FHIR_ClientId": {
        "type": "securestring",
        "metadata": {
            "description": "The FHIR Client Id // Service Principal from Azure"
        }
    },
"FHIR_ClientSecret": {
        "type": "securestring",
        "metadata": {
            "description": "The FHIR secret // Secret from Service Principal in Azure"
        }
    },
"FHIR_URL": {
        "type": "securestring",
        "metadata": {
            "description": "The FHIR uri"
        }
    }
```
