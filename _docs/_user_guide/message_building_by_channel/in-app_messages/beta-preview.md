---
nav_title: Beta
platform: Message_Building_and_Personalization
subplatform: In-App Messages
page_order: 9
hidden: true
desciption: "This reference article covers the new in-app messaging HTML Preview feature."
---

# In-App Messages HTML Preview Beta

Learn about the new Beta Version of custom HTML In-App Messages.

{% alert important %}
This feature is in *Beta*. Ask your Braze team for more information on how to get access.
{% endalert %}

## New Features

### Interactive Preview

The message preview screen now shows a more realistic preview that renders the JavaScript included in your message.

This means you can now preview _and interact_ with your custom messages (i.e. click through pagination, submit forms or surveys, watch JavaScript animations, etc.)

![New HTML In App Preview]({% image_buster /assets/img/iam-beta-javascript-preview.gif %})

{% alert tip %}
We'll ensure that any [`appboyBridge`]({{site.baseurl}}/user_guide/message_building_by_channel/in-app_messages/customize/#javascript-bridge) javascript methods you use in your HTML won't actually update user profiles _while previewing in the dashboard_.
{% endalert %}


### Cross-Channel HTML Messages

This new HTML message type now lets you create one message that can be sent to both mobile and web!

![New HTML In App Message Cross Channel]({% image_buster /assets/img/iam-beta-html-cross-channel.png %})

### Asset Management

Upload campaign assets to the Braze Media Library using a simple drag-and-drop interface.

This new workflow makes it easy to upload a file and copy/paste its URL directly into your HTML.

We've also added the ability to upload additional file types, including:

| File Type | File Extension|
| :-------- | :------------ |
| Font Files| `.ttf`, `.woff`, `.otf`, `.woff2`|
| SVG Images| `.svg`|
| Javascript Files| `.js`|
| CSS Files| `.css`|

{% alert tip %}
Adding files to a campaign's asset list will ensure they are available on mobile devices even if a user has a poor internet connection.
{% endalert %}

### Syntax Highlighting

The code editor now includes Syntax Highlighting with a number of different color themes to choose from.

This helps to easily spot potential code errors directly in the message composer, and better organize your code (using spaces or tabs - whichever side of that argument you're on).

![New HTML In App Message Syntax Highlighting]({% image_buster /assets/img/iam-beta-html-syntax-highlighting.png %})

### Button Tracking Improvements

We've introduced a new [`appboyBridge`][1] JavaScript method (`appboyBridge.logClick(id_string)`) to programatically track button clicks, for scenarios where users are not clicking links, or for tracking buttons after making some API request within a campaign. See our JavaScript [documentation]({{site.baseurl}}/user_guide/message_building_by_channel/in-app_messages/customize/#javascript-bridge) for more details.

Additionally, HTML In-App Messages are no longer limited to recording one button click event per impression.

## Campaign Setup {#instructions}

### SDK Requirements {#supported-sdk-versions}

These Beta features require upgrading to the following Braze SDK version:

* Web SDK v2.5+ [Changelog]({{site.baseurl}}/developer_guide/platform_integration_guides/web/changelog/#250)
* iOS SDK - v3.23.0+ [Changelog]({{site.baseurl}}/developer_guide/platform_integration_guides/ios/changelog/#3230)
* Android SDK - v8.0.0+ [Changelog]({{site.baseurl}}/developer_guide/platform_integration_guides/android/changelog/#800)

{% alert warning %}
Because this message type can only be received by certain newer SDK versions, users that are on unsupported SDK versions will not receive the message. 

Consider adopting this new message type once a significant portion of your user base is reachable, or create a new campaign that only targets supported SDK versions using our new greater-than or less-than app version targeting filter. [Learn More]({{ site.baseurl }}/user_guide/engagement_tools/campaigns/ideas_and_strategies/new_features/#filtering-by-most-recent-app-versions)
{% endalert %}

### New Message Type {#new-message-type}

When creating a "Custom Code" message, choose the new "HTML Upload with Preview" option as shown below:

![New HTML In App Message Beta Dropdown]({% image_buster /assets/img/iam-beta-html-dropdown.gif %})

Keep in mind that your mobile app users need to upgrade to the supported SDK versions in order to receive this message. 

We recommend that you [nudge users to upgrade]({{site.baseurl}}/user_guide/engagement_tools/campaigns/ideas_and_strategies/new_features/) their mobile apps before launching campaigns that depend on newer Braze SDK versions. 

### Uploading Asset Files {#upload-assets}

Use Braze's Media Library to upload and host assets for your custom HTML messages.

We recommend uploading assets to Braze's Media Library for two reasons:

1. Assets added to a campaign via Media Library will allow your messages to be displayed even while the user is offline
2. Assets uploaded to Braze can be more easily re-used across campaigns.

To add _new_ assets to your campaign, use the Drag-and-Drop section to upload a file _and_ add associate the file with this campaign.

You can also add _existing_ assets to your campaign that you've already uploaded to Braze's Media Library.

![New HTML In App Message Asset Uploader]({% image_buster /assets/img/iam-beta-html-asset-uploader.gif %})

Once your assets are added to a campaign, you can use the _Copy Link_ button to store file's URL to your clipboard.

Then, paste the copied asset URL into your HTML as you normally would when referencing a remote asset.

For example, if your HTML references a local asset like `<img src="/cat.png">` (which was common when uploading a zip file), you would change to the newly uploaded asset URL `<img src="https://cdn.braze.com/appboy/communication/assets/image_assets/images/55ef23b46461733bd00d0000/original.?1441735604">`. 

{% alert tip %}
You can press `CTRL+F` or `CMD+F` within the HTML Editor to search within your code!
{% endalert %}

## Providing Feedback

Feedback is encouraged and welcome! 

Please send any feedback or suggestions through to your Braze Customer Success Team.

[1]: {{site.baseurl}}/user_guide/message_building_by_channel/in-app_messages/customize/#javascript-bridge
