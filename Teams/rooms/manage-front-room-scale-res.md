---
title: Remotely configure layout, scale, and resolution on Teams Rooms displays
ms.author: tonysmit
author: tonysmit
ms.reviewer: sohailta
ms.date: 01/24/2023
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
description: Remotely configure the scale, resolution, and default layout of displays on Microsoft Teams Rooms systems.
---

# Remotely configure layout, scale, and resolution on Teams Rooms displays

If you have multiple Teams Rooms systems deployed in your organizations, you can configure display settings such as scale, resolution, and default layout, remotely using an XML configuration file. This XML configuration file can be deployed from a central location to your Teams Rooms systems. When the XML file is deployed to a Teams Rooms system, the configuration settings defined within it will be applied the next time the system is restarted.

For more information about the Teams Rooms XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Set default layout when you have a single display

If you only have one front of room display, you can set the default layout that's used when a meeting starts. To set the default layout, add `SingleFoRDefaultContentLayout` to your XML configuration file with one of the two following options:

- `0` Content only
- `1` Content and people (default)

For example, to default to the "content and people" layout, use the following:

```xml
<SingleFoRDefaultContentLayout>1</SingleFoRDefaultContentLayout>
```

## Set front of room scale and resolution

You can set the scale and resolution for your main front of room display. If you have dual displays, you can and set the scale and resolution for an extended display too.

You can manually set the display resolution on main and extended displays. Those options are `MainFoRDisplayResolution` and `ExtendedFoRDisplayResolution` respectively. Both options accept two numerical values that represent the width and height of a display, separated by a comma. For example, to specify a display resolution of width of 1920 and a height of 1080, the value to enter would be `1920,1080`. If you enter display resolution values that the display doesn't support, the values will be ignored.

You can manually set the display scaling on main and extended displays. Those options are `MainFoRDisplayScaling` and `ExtendedFoRDisplayScaling` respectively. Both options accept the values 100 (recommended), 125, 150, 175, 200, 225, 250, 300, 350, 400, 450, and 500. If you enter a value the display doesn't support, it'll default to the closest supported value.

### Enable customized scale and resolution for front of room displays

To set the scale and resolution for your displays, you first need to tell Teams that you want to do so by adding `<EnableResolutionAndScalingSetting>true</EnableResolutionAndScalingSetting>` to the XML file. After you've added this line to the XML file, you can set the scale and resolution for your main display, and your extended display if you have one.

> [!IMPORTANT]
> If you enable customized scale and resolution and you have dual front of room displays, you need to specify both `MainFoRDisplay` and `ExtendedFoRDisplay` and their respective options. If you don't specify both, the custom configuration will be ignored.

### Set scale and resolution for your main front of room display

To set the scale and resolution for your main front of room display, add the following to your XML configuration file

```xml
<MainFoRDisplay>
      <MainFoRDisplayResolution>1920,1080</MainFoRDisplayResolution> 
      <MainFoRDisplayScaling>100</MainFoRDisplayScaling> 
</MainFoRDisplay>
```

### Set scale and resolution for your extended front of room display

To set the scale and resolution for your extended front of room display, add the following to your XML configuration file:

```xml
<ExtendedFoRDisplay> 
    <ExtendedFoRDisplayResolution>1920,1080</ExtendedFoRDisplayResolution> 
    <ExtendedFoRDisplayScaling>100</ExtendedFoRDisplayScaling> 
</ExtendedFoRDisplay>  
```
