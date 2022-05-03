---
title: Categorical Axis
page_title: .NET MAUI Chart Documentation | Categorical Axis
slug: axes-categorical-axis
description: Check our &quot;Categorical Axis&quot; documentation article for Telerik Chart for .NET MAUI.
position: 2
previous_url: /controls/chart/axes/axes-categorical-axis
---

# Categorical Axis

When the Cartesian Chart visualizes Categorical Series, it needs an axis that can represents the different categories. Categories are built depending on the `CategoryBinding` value of each categorical data point in the owning Categorical Series. The axis is divided into discrete slots and each data point is visualized in the slot corresponding to its categorical value.

The `CategoricalAxis` inherits from the base `Axis` class. For more information, refer to the article on [inherited properties]({% slug axes-overview %}).

## Features

The Categorical Axis exposes the following properties:

- `GapLength`&mdash;Defines the distance (in logical units [0,1]) between two adjacent categories. The default value is `0.3`. For example, if you have Bar Series, you can decrease the space between the bars from the different categories by setting the `GapLength` to a value lower than `0.3`.
- `MajorTickInterval`&mdash;Defines the step at which major ticks are generated. The default value is `1`. This property will also affect axis labels as they are generated based on a major tick basis.
- `PlotMode`&mdash;Defines the strategy used to position data points along the axis category slots. The possible values are `BetweenTicks` and `OnTicks`.
- `MajorTickBackgroundColor`&mdash;Specifies the major ticks color.
- `MajorTickThickness`&mdash;Specifies the thickness of the major ticks.

## Example

The following example shows how to format the axis labels on the Categorical Axis.

1. First, create the needed business objects:

 ```C#
public class CategoricalData
{
    public object Category { get; set; }

    public double Value { get; set; }
}
```

1. Then, create a `ViewModel`:

 ```C#
public class CategoricalDataViewModel
{
    public ObservableCollection<CategoricalData> Data { get; set; }

    public CategoricalDataViewModel()
    {
        this.Data = GetCategoricalData();
    }

    private static ObservableCollection<CategoricalData> GetCategoricalData()
    {
        var data = new ObservableCollection<CategoricalData>
        {
            new CategoricalData { Category = "A", Value = 101 },
            new CategoricalData { Category = "B", Value = 45 },
            new CategoricalData { Category = "C", Value = 77 },
            new CategoricalData { Category = "D", Value = 15 },
            new CategoricalData { Category = "E", Value = 56 },
        };
        return data;
    }
}
 ```

1. Finally, use the following snippet to declare the `RadChart` in XAML or in C#:

 ```XAML
    <telerikChart:RadCartesianChart>
	  <telerikChart:RadCartesianChart.BindingContext>
	    <local:CategoricalDataViewModel/>
	  </telerikChart:RadCartesianChart.BindingContext>
	  <telerikChart:RadCartesianChart.HorizontalAxis>
	    <telerikChart:CategoricalAxis PlotMode="OnTicks"
								      MajorTickInterval="2"
									  GapLength="0.5"/>
	  </telerikChart:RadCartesianChart.HorizontalAxis>
	  <telerikChart:RadCartesianChart.VerticalAxis>
	    <telerikChart:NumericalAxis LabelFitMode="MultiLine"/>
	  </telerikChart:RadCartesianChart.VerticalAxis>
	  <telerikChart:RadCartesianChart.Series>
	    <telerikChart:BarSeries ItemsSource="{Binding Data}"
		                        ValueBinding="Value"
                                CategoryBinding="Category"/>
	  </telerikChart:RadCartesianChart.Series>
    </telerikChart:RadCartesianChart>
 ```


The following image shows the end result.

![CategoricalAxis](images/axes-categorical-axis-example.png)

## See Also

- [Axis Overview]({%slug axes-overview%})
- [Numerical Axis]({%slug axes-numerical-axis%})
- [DateTimeContinuous Axis]({%slug axes-date-time-continuous-axis%})