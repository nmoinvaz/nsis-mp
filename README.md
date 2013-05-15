MixPanel Analytics for NSIS

This script will allow you to add mixpanel event tracking into your NSIS installer. It is useful for tracking installer based events such as the number of successful installs that occured, or the number of offers accepted, or the number of users who clicked the donate button.

Specify the include at the top of your nsh script:

```
!include "mp.nsh"
```

To track an event use the following

```
!insertmacro MixPanelAnalytics "YOUR_TOKEN" "Event" "Action"
```

Example events to track:

```
Function .onInit
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Install" "Started"
FunctionEnd
Function .onInstFailed
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Install" "Failed"
FunctionEnd
Function .onInstSuccess
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Install" "Success"
FunctionEnd
Function .onGUIEnd
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Install" "Ended"
FunctionEnd

Function un.onInit
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Uninstall" "Started"
FunctionEnd
Function un.onUninstFailed
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Uninstall" "Failed"
FunctionEnd
Function un.onUninstSuccess
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Uninstall" "Success"
FunctionEnd
Function un.onGUIEnd
    !insertmacro MixPanelAnalytics "YOUR_TOKEN" "Uninstall" "Ended"
FunctionEnd
```
This script requires the use of [LogicLib](http://nsis.sourceforge.net/LogicLib) and [inetc](http://nsis.sourceforge.net/Inetc_plug-in) and [base64](https://github.com/nmoinvaz/nsis-base64) plugins. Tested only with the non-Unicode version of NSIS.

