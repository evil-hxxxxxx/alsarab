# 1. Simple Update Dialog
````json
{
  "dialogTitle": "Update Available 🚀",
  "dialogSubtitle": "A brand-new update is here! 🎉\n\n✅ **Performance Enhancements** – Faster and smoother experience.\n🐞 **Critical Bug Fixes** – Say goodbye to annoying issues.\n✨ **Exciting New Features** – Discover improved functionality and tools.\n\nWe highly recommend updating now to enjoy the best performance, enhanced security, and all the latest features!\n\n🔄 **Tap 'Update Now' to get started!**",
  "dialogBtnMainTxt": "Update Now",
  "dialogBtnMainClick": "browser",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "dialogOption": "update",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "false",
  "dialogBtnMain": "true",
  "customDialogAccent": "#4562EA"
}
````

# 2. Dialog with Two Buttons (Main + Extra)
````json
{
  "dialogTitle": "Update Available 🚀",
  "dialogSubtitle": "A brand-new update is here! 🎉",
  "dialogBtnMainTxt": "Update Now",
  "dialogBtnExtraTxt": "Later",
  "dialogBtnMainClick": "browser",
  "dialogBtnExtraClick": "dismiss",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "dialogOption": "update",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "true",
  "dialogBtnMain": "true",
  "customDialogAccent": "#4562EA"
}
````

# 3. Exit Dialog
````json
{
  "dialogTitle": "Important Notice",
  "dialogSubtitle": "Please subscribe to our channel",
  "dialogBtnMainTxt": "Subscribe",
  "dialogBtnExtraTxt": "Exit",
  "dialogBtnMainClick": "browser",
  "dialogBtnExtraClick": "exit",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "dialogOption": "warning",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "true",
  "dialogBtnMain": "true",
  "customDialogAccent": "#BD081C"
}
````

# 4. Custom Dialog with Two Links
````json
{
  "dialogTitle": "Our Channels 📱",
  "dialogSubtitle": "Subscribe to both channels!",
  "dialogBtnMainTxt": "Main Channel",
  "dialogBtnExtraTxt": "Second Channel",
  "dialogBtnMainClick": "browser",
  "dialogBtnExtraClick": "browser",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "openLinkExtra": "https://www.youtube.com/@AhmedElEmberator2",
  "dialogOption": "custom",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "true",
  "dialogBtnMain": "true",
  "customDialogAccent": "#4562EA",
  "customDialogIcon": "https://example.com/icon.png"
}
````

# 5. Warning Dialog
````json
{
  "dialogTitle": "⚠️ Warning",
  "dialogSubtitle": "Important notice for users",
  "dialogBtnMainTxt": "Visit Channel",
  "dialogBtnMainClick": "browser",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "dialogOption": "warning",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "false",
  "dialogBtnMain": "true",
  "customDialogAccent": "#BD081C"
}
````

Key Features in Each Case:
1. `dialogBtnMainClick`: "browser", "exit", or "dismiss"
2. `dialogBtnExtraClick`: "browser", "exit", or "dismiss"
3. `dialogOption`: "update", "warning", "message", or "custom"
4. `isCancelable`: Controls if dialog can be dismissed
5. `isOneTime`: Controls if dialog shows every time
6. `customDialogAccent`: Different colors for different types (#4562EA for normal, #BD081C for warning)


# JSON structure with a focus on exit functionality:

````json
{
  "dialogTitle": "Update Available 🚀",
  "dialogSubtitle": "A brand-new update is here! 🎉\n\n✅ **Performance Enhancements** – Faster and smoother experience.\n🐞 **Critical Bug Fixes** – Say goodbye to annoying issues.\n✨ **Exciting New Features** – Discover improved functionality and tools.\n\nWe highly recommend updating now to enjoy the best performance, enhanced security, and all the latest features!\n\n🔄 **Tap 'Update Now' to get started!**",
  "dialogBtnMainTxt": "Subscribe",
  "dialogBtnExtraTxt": "Exit",
  "dialogBtnMainClick": "browser", 
  "dialogBtnExtraClick": "exit",
  "openLinkMain": "https://www.youtube.com/@AhmedElEmberator",
  "dialogOption": "warning",
  "newVersion": "2.47",
  "isOneTime": "false",
  "isCancelable": "false",
  "dialogBtnExtra": "true",
  "dialogBtnMain": "true",
  "customDialogAccent": "#BD081C",
  "customDialogBack": "#FFFFFF", 
  "customDialogRound": "25",
  "customDialogMainTxtColor": "#212121",
  "customDialogBtnTxtColor": "#FFFFFF",
  "customDialogBtnExtraColor": "#BD081C",
  "customDialogBtnExtraTxtColor": "#FFFFFF"
}
````

# particularly around the `isOneTimeKey` and `isOneTime` handling, here are the key notes regarding one-time functionality:

# One-Time Display Notes

1. `isOneTime` field can be used for:
- Update dialogs
- Warning messages 
- Custom notifications
- Information popups

2. Key Code Paths:
```smali
// Checks if one-time is enabled
move-object/from16 v0, p0
iget-object v10, v0, BackupPro;->UpdatifyMap:Ljava/util/HashMap;
const-string v15, "isOneTime" 
invoke-virtual {v10, v15}, Ljava/util/HashMap;->get(Ljava/lang/Object;)Ljava/lang/Object;
```

3. SharedPreferences Storage:
- Uses "UCSP" preferences file
- Stores `isOneTimeKey` as unique identifier
- Checks against stored key to determine if shown before

4. All Dialog Types Support One-Time:
```json
// Example for any dialog type
{
  "dialogOption": "update|warning|message|custom",
  "isOneTime": "true",
  "isOneTimeKey": "unique_key_here"
}
```

5. Implementation Notes:
- All dialog types can use one-time display
- Each needs unique `isOneTimeKey` value
- Setting `isOneTime` to "false" shows dialog every time
- Keys should be unique per dialog/message

6. Example Usage:
```json
{
  "dialogOption": "warning",
  "isOneTime": "true",
  "isOneTimeKey": "warning_key_123",
  // ...other dialog properties
}
```

So yes, all dialog types can implement one-time display functionality through proper use of `isOneTime` and `isOneTimeKey` fields.
