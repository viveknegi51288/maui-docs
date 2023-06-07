---
title: Hyperlink Support
page_title: .NET MAUI RichTextEditor Documentation - Hyperlink Support
description: Review the hyperlink support documentation article for Telerik RichTextEditor for .NET MAUI control.
position: 2
slug: richtexteditor-hyperlink-support
---

# Hyperlink Support

RichTextEditor provides built-in support for creating and managing hyperlinks. Through the exposed commands related to hyperlinks, namely ApplyHyperlinkCommand, RemoveHyperlinkCommand, and OpenHyperlinkCommand, users can manipulate the hyperlinks inside the RichTextEditor content.

In addition, RichTextEditorToolbar exposes predefined toolbar items wired to the hyperlink commands. 

* `RichTextEditorAddHyperlinkToolbarItem`&mdash;Opens a popup to enter Url information and executes action to add a hyperlink for the current selection.
* `RichTextEditorAddOrEditHyperlinkToolbarItem`&mdash;Opens a popup to enter Url information and executes action to add or edit a hyperlink for the current selection.
* `RichTextEditorHyperlinkNavigationToolbarItem`&mdash;This toolbar item adds or edits hyperlinks depending whether hyperlink is selected. If hyperlink is selected, the editor navigates to sub toolbar items for operations related to hyperlink. If hyperlink is not selected a popup with a dialog is displayed to enter Url information and add a hyperlink for the current selection.

## Additional Toolbar items for hyperlink operations

The `RichTextEditorHyperlinkNavigationToolbarItem` has the following items:

* `RichTextEditorEditHyperlinkToolbarItem`&mdash;Edits the hyperlink from the current selection.
* `RichTextEditorRemoveHyperlinkToolbarItem`&mdash;Removes the hyperlink from the current selection.
* `RichTextEditorOpenHyperlinkToolbarItem`&mdash;Navigates to the Url.

![.NET MAUI RichTextEditor Hyperlink Navigation](images/rte-hyperlink-toolbar.png)

And how the `RichTextEditorEditHyperlinkToolbarItem` looks on Mobile:

![.NET MAUI RichTextEditor Hyperlink Navigation](images/rte-hyperlink-edit.png)

For more details on this check [RichTextEditor Toolbar]({%slug richtexteditor-toolbar%}#predefined-toolbar-items) topic.

## Methods

You can also take advantage of the following API related to hyperlinks:

* `GetHyperlinkAsync` method - returns asynchronously a RichTextHyperlink under the caret in the editor (or `null` in case there is no hyperlink). The <code>RichTextHyperlink</code> object contains the `Url` and `Title` of the link;

## Hyperlink Error Handling

In case users try to open invalid urls (for example, the url is not absolute, the domain does not exist or is incomplete, etc) the following message is shown by default indicating there is an error with the url:

![.NET MAUI RichTextEditor Hyperlink Error Handling](images/rte-hyperlink-error-handling.png)

You can override the default behavior by handling the RichTextEditor's **OpenHyperlinkError** event:

* `OpenHyperlinkError` event&mdash;Raised when users try to open invalid urls in the editor. The OpenHyperlinkError event handler receives two parameters:

	* The <code>Sender</code> which is the RichTextEditor control;
	* OpenHyperlinkErrorEventArgs provides the following properties:
		* <code>Error</code> - of type System.Exception, can be used to get the exact error message;
		* <code>Url</code> - of type string, defining the url of the hyperlink;
		* <code>Handled</code> - boolean property indicating whether the event is handled.

Subscribe to the event, set <code>Handled</code> property of the event args to *True* to prevent the default message and add custom implementation. 

Here is a quick example on the OpenHyperlinkError event usage:

<snippet id='richtexteditor-hyperlinkerrorhandling-xaml' />

And the event handler which shows a custom message:

<snippet id='richtexteditor-hyperlinkerrorhandling-code' />

>important For the RichTextEditor Hyperlink Error Handling example refer to the [SDKBrowser Demo Application]({%slug sdkbrowser-app%}) RichTextEditor -> Events category.

## See Also

- [Commands]({%slug richtexteditor-commands%})
- [Configure the RichTextEditor]({%slug richtexteditor-configuration%})
- [Events]({%slug richtexteditor-events%})
- [Working with images]({%slug richtexteditor-images-overview%})