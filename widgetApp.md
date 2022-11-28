# What's New

<!-- Landing page -->

The latest release of WidgetApp includes loads of new features to help you design your best Things faster and easier than ever!

- To get straight back to creating with our new tools, check out the :paintbrush:[User Guide](#paintbrush-user-guide)
- For more power in the backend changes, jump down to the :briefcase:[Admin Guide](#briefcase-admin-guide) 
- Or for that nitty-gritty technical detail, go for the :wrench:[API Guide](#wrench-api-guide)

For a full guide on using WidgetApp, check out the guides on our [Help Centre](external_link_here)

## :paintbrush: User Guide
<!-- User guide, for non-technical domain experts in Things on how to use the app. -->
Introducing Live ThingBuilding! 
Collaborate in real-time with people within your organisation on new or existing Things.

![animated image of a screen capture of two cursors editing a Thing - to be recorded]()

You can invite other users to work on your Things, and this is all securely managed behind the scenes to make sure everyone can only see what they're supposed to. 
If your team has opted in for live collaboration, you don't need do anything further. Just log in as normal and you can start creating together today! 

## :briefcase: Admin Guide
<!-- Administrator guide, for technical support staff on how to install, configure, and maintain the web server. -->
### What is the Streaming Frontend?
The latest version of WidgetApp allows multiple users to work on the same Thing at the same time. 
The Streaming frontend (SFE) propagates changes as quickly as possible so all clients can see them using Streaming API. 
This feature is optional and specifically approved per User Group - OAuth2.0 access tokens are used to manage access. 
This does not affect preexisting authentication protocols in WidgetApp Frontend (WFE).

Similarly, WFE generally handles existing API requests as per previous versions. 
However, for authorized connections using Streaming API it hands over to the new Streaming Frontend (SFE). 
SFE manages the session as per WFE, but with Streaming API capabilities.

### How does Streaming API work?
Streaming API runs over websockets - different services can use the same websocket connection. 
Most user actions, like search or scrolling, work by calling `_ajax/` endpoints.
External systems that use SFE can connect using `wss://www.widgetapp.com/_stream`.
They must listen on port 200 for stream messages from any `widgetApp_useraction_xxx` APIs (such as `widgetApp_useraction_refresh()`, `widgetApp_useraction_edit()`, etc.).

### Managing SFE
Of course, SFE and Streaming API processes add to server load due to their frequent updates.
The default setup is to launch one SFE on startup, with another started in parallel for every 10 Streaming API clients.

We recommend that you monitor `_sfe` and `_stream` processes for resource use (CPU, memory, etc) to ensure they are operating within your infrastructure's capacity.
You should restart any processes that go rogue (>~50% load).
Killed `_stream` processes are automatically restarted for existing SFE instances.
To restart `_sfe` instances, use the following command: 
```
widgetapp_admin -process _sfe -n <num_instances> -start
```

## :wrench: API Guide
<!-- API guide, for third-party developers on how to interface with WidgetApp programmatically. -->
The latest release introduces the new Streaming Frontend (SFE) in addition to the existing WidgetApp Frontend (WFE). 
WFE continues to handle existing API requests as per previous versions.
SFE allows real-time collaboration and uses the new Streaming API for authorised connections. 

Streaming API runs over websockets - different services can use the same websocket connection.
OAuth2.0 tokens are required to access Streaming API.
Most user actions, like search or scrolling, work by calling `_ajax/` endpoints *[link out to a complete reference]*.
External systems connect using `wss://www.widgetapp.com/_stream` and must listen on port 200 for stream messages from any `widgetApp_useraction_xxx` APIs *[link out to a complete reference]*.