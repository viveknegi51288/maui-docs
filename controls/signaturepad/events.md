---
title: Events
page_title: .NET MAUI SignaturePad Documentation - Events
description: "Review the Events article of the Telerik SignaturePad for .NET MAUI control."
position: 9
tags: sing pad, signature, .net maui, dotnet, sign, signature pad
slug: signaturepad-events
---

# .NET MAUI SignaturePad Events

The SignaturePad for .NET MAUI exposes the following events: 

* `StrokeStarted` event is raised when a new stroke is started. The `StrokeStarted` event handler receives two parameters: 
	* The `Sender` which is of type `Telerik.Maui.Controls.RadSignaturePad`. 
	* and `EventArgs` 

* `StrokeCompleted` event is raised when a new stroke is completed. The `StrokeCompleted` event handler receives two parameters:
	* The `Sender` which is of type `Telerik.Maui.Controls.RadSignaturePad`.
	* and `EventArgs` 

* `Cleared` event is raised when the surface of Telerik.Maui.Controls.RadSignaturePad is cleared.

## Example

The example contains a **X** Button, two Labels and a RadSignaturePad. The control's definition in XAML:

<snippet id='signaturepad-events'/>

Add the following namespace:

<snippet id='xmlns-telerikinput'/>

Let's add the events:

The `RadSignaturePad.StrokeStarted` event. When stroke starts we will display a timestamp using a Label:

<snippet id='signaturepad-strokestarted-event'/>

The `RadSignaturePad.StrokeCompleted` event. When stroke completes the timespamp Label text is udated.

<snippet id='signaturepad-strokecompleted-event'/>

The `SignaturePad.Cleared` event, When `Cleared` event is fired, Label with `Text="Cleared"` is displayed.

<snippet id='signaturepad-cleared-event'/>

![.NET MAUI SignaturePad Events](images/signatrue-events.gif)

>important For the SignaturePad Events example refer to the [SDKBrowser Demo Application]({%slug sdkbrowser-app%}).

## See Also

- [Configure the Signature]({% slug signaturepad-configuration%})
- [Commands]({% slug signaturepad-commands%})
- [Save Signature]({% slug signaturepad-saving-options%})