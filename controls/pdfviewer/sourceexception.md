---
title: Source Exception Handling
page_title: .NET MAUI PdfViewer Documentation - Source Exception Handling
description: Check our &quot;Source Exception Handling&quot; documentation article for Telerik PdfViewer for .NET MAUI control.
position: 8
slug: pdfviewer-sourceexception
---

# Source Exception Handling

In certain cases PdfViewer will not be able to load the passed Pdf document - it can be due to invalid stream/inaccessible URL or some invalid data in the document itself. RadPdfViewer provides a way to catch these cases through its **SourceException** event. In addition, you could show a user-friendly message to the users through **SourceExceptionTemplate**.

Check the example below which shows how to use the RadPdfViewer API for handling source exceptions.

**1,.** Define RadPdfViewer control and apply a SourceExceptionTemplate. The snippet below demonstrates a sample template with only one Label which holds the message. 

<snippet id='pdfviewer-source-exception-xaml' />

**2.** Add the `telerik` namespace:

```XAML
xmlns:telerik="http://schemas.telerik.com/2022/xaml/maui"
```

**3.** And the SourceException event handler:

<snippet id='pdfviewer-sourceexception-eventhandler' />

Check below how the defined SourceTemplateException looks:

![.NET MAUI PdfViewer SourceException](images/pdfviewer-sourceexceptiontemplate.png)

> For the PdfViewer SourceException example, go to the [SDKBrowser Demo Application]({%slug sdkbrowser-app%}) and navigate to PdfViewer -> Features category.

## See Also

- [PdfViewer Toolbar]({%slug pdfviewer-toolbar%})