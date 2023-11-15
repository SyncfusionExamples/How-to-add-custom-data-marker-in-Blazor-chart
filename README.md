# How-to-add-custom-data-marker-in-Blazor-chart
 
 
In this article, we will discuss about how to use the custom view as a chart data marker and how to change data marker appearance based on the Y plot?

**Customizing data marker appearance using OnPointRender event**

In [Blazor Chart](https://www.syncfusion.com/blazor-components/blazor-charts) , the data marker appearance can be changed based on Y value. Blazor chart provide [OnPointRender](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartEvents.html#Syncfusion_Blazor_Charts_ChartEvents_OnPointRender) event for customizing the property before rendering of each point.

The following properties are available in the [PointRenderEventArgs](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html).

•	[Border](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Border) – Specifies the color and the width of the point border.

•	[Fill](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Fill) – Specifies the fill color of the point.

•	[Height](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Height) – Specifies the current point’s height.

•	[Shape](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Shape) – Specifies the marker shape of the point.

•	[Width](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Width) – Specifies the current point’s width.

We can customize the marker appearance  based on Y value by specifying the [Shape](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Shape) , [Border](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Border) and [Fill](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html#Syncfusion_Blazor_Charts_PointRenderEventArgs_Fill) property of the [PointRenderEventArgs](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.PointRenderEventArgs.html).

The below code example illustrates the marker appearance based on Y value. The Border color is changes to red and green by comparing with previous point of the series.

**C#**

```cshtml

@using Syncfusion.Blazor.Charts

<SfChart>   
    <ChartEvents OnPointRender="@PointRender"></ChartEvents>
    <ChartSeriesCollection>
        <ChartSeries DataSource="@ConsumerReports" XName="X" YName="Y" Type="ChartSeriesType.Spline">
            <ChartMarker Visible="true" Height="10" Width="10" />
        </ChartSeries>
    </ChartSeriesCollection>
</SfChart>

@code {

    double temp = 0;

    public class ChartData
    {
        public double X { get; set; }
        public double Y { get; set; }
    }

    public List<ChartData> ConsumerReports = new List<ChartData>
    {
        new ChartData{ X= 2005, Y= 15 },
        new ChartData{ X= 2006, Y= 20 },
        new ChartData{ X= 2007, Y= 15 },
        new ChartData{ X= 2008, Y= 20 },
        new ChartData{ X= 2009, Y= 25 },
        new ChartData{ X= 2010, Y= 30 },
        new ChartData{ X= 2011, Y= 25 },
        new ChartData{ X= 2012, Y= 30 },
        new ChartData{ X= 2013, Y= 35 },
        new ChartData{ X= 2014, Y= 30 },
        new ChartData{ X= 2015, Y= 25 }
    };

    public void PointRender(PointRenderEventArgs args)
    {
        if (args.Point.YValue >= temp)
        {
            args.Border.Color = "green";
            temp = args.Point.YValue;
        }

        if (args.Point.YValue < temp)
        {
            args.Border.Color = "red";
            temp = args.Point.YValue;
        }        
    }
}

```


The following screenshot illustrate the output of the above code snippet.

**Output:**

![](/marker-appearence.png)

**Conclusion**

I hope you enjoyed learning how to show different data marker appearance based on conditions in Blazor Chart Component.

You can refer to our [Blazor Chart feature tour](https://www.syncfusion.com/blazor-components/blazor-charts) page to know about its other groundbreaking feature representations and [documentation](https://blazor.syncfusion.com/documentation/chart/getting-started), and how to quickly get started for configuration specifications. You can also explore our [Blazor Chart example](https://blazor.syncfusion.com/demos/chart/line?theme=bootstrap5) to understand how to create and manipulate data.

For current customers, you can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/blazor) to check out our other controls.

If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [support portal](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/blazor-components?control=charts). We are always happy to assist you!

