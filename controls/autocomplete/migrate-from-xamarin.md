---
title: Migrate from Xamarin.Forms
page_title: .NET MAUI AutoComplete Documentation - Migrate from Xamarin
description: "Learn how to migrate from Xamarin.Forms AutoCompleteView to .NET MAUI AutoCompolete control."
position: 2
slug: autocomplete-migrate-from-xamarin
---

# Migrate from Xamarin.Forms

Overall, Telerik .NET MAUI AutoComplete control preserves the same API as Xamarin.Forms AutoCompleteView with a few changes and improvements listed in the table below:

| Xamarin AutoCompleteView | .NET MAUI AutoComplete |
| ------------- | --------------- |
| control name - `AutoCompleteView` | control name - `AutoComplete` |
| `WatermarkText` | `Placeholder` |
| `WatermarkTextColor` | `PlaceholderColor` |
| `SuggestionItemTextColor` | `SuggestionItemHighlightText` |
| Uses Xamarin.Forms ListView for the Suggestion List | Uses .NET MAUI CollectionView for the Suggestion List |
| `SuggestionItemLabel` |  |
| `ImagePath` | - |

## See Also