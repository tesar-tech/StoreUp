# Store Up

<a href='//www.microsoft.com/store/apps/9PH5NNZ5BXFQ?cid=storebadge&ocid=badge'><img src='https://assets.windowsphone.com/13484911-a6ab-4170-8b7e-795c1e8b4165/English_get_L_InvariantCulture_Default.png' alt='English badge' width="100" /></a>


App for testing automatic store update with azure-pipelines. (just blank uwp app with no functionality).

[![Build Status](https://tjkod.visualstudio.com/StoreUp/_apis/build/status/tesar-tech.StoreUp?branchName=master&jobName=Job)](https://tjkod.visualstudio.com/StoreUp/_build/latest?definitionId=1&branchName=master)


Using [windows-dev-center-vsts-extension](https://github.com/microsoft/windows-dev-center-vsts-extension). There are also pretty exhaustive instructions about setting and usage.

Pushing to master causes package update in store. It is also able to update store listing like description, screenshots, etc. (in `NoApp/Store/appMetadata` folder). See [azure-pipelines.yml](https://github.com/tesar-tech/StoreUp/blob/master/azure-pipelines.yml) file for more details.

## Quick HowTo for new projects

From UWP source code to app in the Store (about 1.5 hour).

- First package must be uploaded manualy.
  - Create new app in store (about 20 mins):
    - Need to create Privacy Policy file (check [this file](https://github.com/tesar-tech/StoreUp/blob/master/NoApp/PrivacyStatements.md) for simple statement)
    - Need to upload first package.
      - No default images are allowed in Stored. I recommend creating one 400x400 png image and use Package.appmanifest -> Visual assets -> Generator.
      - Associate package with Store (right click to project -> Publish)
      - Create App package(s), Run certification toolkit (recommended). Upload .msixupload file.
      - Dont't forget to uncheck Windows 10 Mobile if you don't plan to do so (W10M doesn't support new Target versions).
    - Provide at least one screen shot. [Sizer](https://chocolatey.org/packages/sizer) will help you with setting recommended size of window for screenshot.
- Credentinals for automatic publish must be already obtained. [Here](https://github.com/microsoft/windows-dev-center-vsts-extension) is how to do it.
- In AzureDevOps you need to add new **Service Connection** (under Project settings -> Pipelines).
  - Select Win Dev Center and fill tenant Id, clinet Id, secret and name (in StoreUp sample it's called `NaWinDevCenter`).
- Copy `azure-pipelines.yml` file and edit few lines:
  - appId in storePublish task
  - Provide metadata file or delete some rows in storePublish task (metadataUpdateMethod,metadataPath,updateImages)
    - StoreUp metadata file is in NoApp/Store folder structure, also with screenshots.
- Push code to your repo. 
- Set pipeline in AzureDevops
  