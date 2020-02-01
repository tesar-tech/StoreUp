# Store Up

<a href='//www.microsoft.com/store/apps/9PH5NNZ5BXFQ?cid=storebadge&ocid=badge'><img src='https://assets.windowsphone.com/13484911-a6ab-4170-8b7e-795c1e8b4165/English_get_L_InvariantCulture_Default.png' alt='English badge' width="100" /></a>


App for testing automatic store update with azure-pipelines. (just blank uwp app with no functionality).

[![Build Status](https://tjkod.visualstudio.com/StoreUp/_apis/build/status/tesar-tech.StoreUp?branchName=master)](https://tjkod.visualstudio.com/StoreUp/_build/latest?definitionId=1&branchName=master)


Using [windows-dev-center-vsts-extension](https://github.com/microsoft/windows-dev-center-vsts-extension). There are also pretty exhaustive instructions about setting and usage.

Pushing to master causes package update in store. It is also able to update store listing like description, screenshots, etc. (in `NoApp/Store/appMetadata` folder). See [azure-pipelines.yml](https://github.com/tesar-tech/StoreUp/blob/master/azure-pipelines.yml) file for more details.