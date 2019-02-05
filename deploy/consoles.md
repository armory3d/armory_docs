# Deploying to consoles

## Native

If you have access to the PS4, Xbox One or Switch console SDK, contact us to get access to the Kha backends. Due to the nature of console development, a proof that you are a registered Microsoft / Nintendo / Sony developer is required. Afterwards, the Kha console backends are provided for free.


## Xbox (Universal Windows Platform)

Create a new preset in `Properties - Render - Armory Exporter` and select `Custom` target. Enter `windowsapp` into `Khamake` field. Hit `Publish` to export Visual Studio project files.

To proceed, install [Visual Studio](https://www.visualstudio.com/vs/community/). Make sure to install components for developing UWP applications. Once installed, open the project located at *blend_file_location/build_projectname/windowsapp-build/projectname.sln*.

![](/deploy/img/xbox/1.png)

Next, you will need to set-up your Xbox for windows app development. Follow [this guide](https://docs.microsoft.com/en-us/windows/uwp/xbox-apps/getting-started). 

![](/deploy/img/xbox/2.png)
