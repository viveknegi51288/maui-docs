---
title: Customize PieChart Series Text, Color and FontSize
description: 
type: how-to
page_title: Label Customization for Chart Pie Series
slug: chart-pieseries-customization
position: 
tags: chart, pie series, label customization, textcolor, fornsize
ticketid: 1618857
res_type: kb
---

## Environment
<table>
    <tbody>
        <tr>
            <td>Product Version</td>
            <td></td>
        </tr>
        <tr>
            <td>Product</td>
            <td>PieChart for MAUI</td>
        </tr>
    </tbody>
</table>


## Description

This article described how to customize the text, color, font size of the chart PieSeries.

## Solution

For this purpose you have to use the native chart. 

**1.** Chart definition in XAML

```XAML
<telerik:RadPieChart x:Name="chart" HandlerChanged="chart_HandlerChanged">
    <telerik:RadPieChart.BindingContext>
        <local:ViewModel />
    </telerik:RadPieChart.BindingContext>
    <telerik:RadPieChart.Series>
        <telerik:PieSeries ShowLabels="True"
                    RadiusFactor="0.8"
                    ValueBinding="Value"
                    ItemsSource="{Binding Data}" />
    </telerik:RadPieChart.Series>
</telerik:RadPieChart>
```

**2.** The namespace

```XAML
xmlns:telerik="http://schemas.telerik.com/2022/xaml/maui"
```

**3.** DataModel and ViewModel

```C#
public class CategoricalData
{
    public object Category { get; set; }
    public double Value { get; set; }
}

public class ViewModel
{
    public ObservableCollection<CategoricalData> Data { get; set; }

    public ViewModel()
    {
        this.Data = GetCategoricalData();
    }

    private static ObservableCollection<CategoricalData> GetCategoricalData()
    {
        var data = new ObservableCollection<CategoricalData>
    {
        new CategoricalData { Category = "Greenings", Value = 52 },
        new CategoricalData { Category = "Perfecto", Value = 19 },
        new CategoricalData { Category = "NearBy", Value = 82 },
        new CategoricalData { Category = "Family", Value = 23 },
        new CategoricalData { Category = "Fresh", Value = 56 },
    };
        return data;
    }
}
```

**4.** Subscribe to the `Chart.HandlerChanged` event to access the native chart and implement the customizations per platform: 

```C#
private void chart_HandlerChanged(object sender, EventArgs e)
{
    this.UpdateChart();
}

private void UpdateChart()
{
    var platformView = this.chart.Handler.PlatformView;

    // Implementation on Android
#if ANDROID
    var platformChart = (Com.Telerik.Widget.Chart.Visualization.PieChart.RadPieChartView)platformView;
    var platformSeries = (Com.Telerik.Widget.Chart.Visualization.PieChart.PieSeries)platformChart.Series.Get(0);

    platformSeries.LabelFillColor = Android.Graphics.Color.Red;
    platformSeries.LabelTextColor = Android.Graphics.Color.Blue;

// Implementation on MacCatalyst and iOS
#elif IOS || MACCATALYST
    var platformChart = (Telerik.Maui.Controls.Compatibility.ChartRenderer.iOS.TKExtendedChart)platformView;
    var platformSeries = (TelerikUI.TKChartPieSeries)platformChart.Series[0];
    platformSeries.Style.PointLabelStyle.TextColor = UIKit.UIColor.Green;
    platformSeries.Style.PointLabelStyle.TextHidden = false;
    platformSeries.Style.PointLabelStyle.StringFormat = "$ %.0f";

    // Implementation on WInUI
#elif WINDOWS
    var platformChart = (Telerik.UI.Xaml.Controls.Chart.RadPieChart)platformView;
    var platformSeries = (Telerik.UI.Xaml.Controls.Chart.PieSeries)platformChart.Series[0];
    platformSeries.LabelDefinitions.Clear();
    platformSeries.LabelDefinitions.Add(new Telerik.UI.Xaml.Controls.Chart.ChartSeriesLabelDefinition 
    { 
            
        LabelTemplate = MauiWinUIApplication.Current.Resources["PieLabelTemplate"] as Microsoft.UI.Xaml.DataTemplate
});
#endif
}
```