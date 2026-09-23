# How to Add Custom Data Marker in Blazor Chart

## Overview

This sample demonstrates how to customize data marker appearance in a Syncfusion [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts) component by using the `OnPointRender` event. During point rendering, the application evaluates each data point and dynamically updates marker border styling based on the current Y-value relative to the previously rendered point.

The implementation uses a spline chart series and a collection of chart data objects to visualize trend changes. By modifying marker properties during rendering, developers can highlight increases and decreases directly within the chart without altering the underlying data source.

## Key Features

- Uses the `SfChart` component to visualize yearly data.
- Configures a spline series through the `ChartSeries` component with `Type="ChartSeriesType.Spline"`.
- Binds chart data using the `DataSource`, `XName`, and `YName` properties.
- Displays markers using the `ChartMarker` configuration.
- Handles the `OnPointRender` event through the `ChartEvents` component.
- Uses the `PointRender(PointRenderEventArgs args)` method to customize marker rendering before each point is displayed.
- Accesses `args.Point.YValue` to evaluate the current data point.
- Updates `args.Border.Color` dynamically based on comparison with the previously rendered point.
- Demonstrates conditional marker styling for upward and downward trends.
- Uses a strongly typed `ChartData` model as the chart data source.

## Prerequisites

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) or [Visual Studio Code](https://code.visualstudio.com/)
- [.NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet) compatible with the project's target framework

## How to Run the Project

**Visual Studio 2022**

1. Clone or download this repository.
2. Open the project file:

   `MarkerAppearance/MarkerAppearance.csproj`

3. Restore NuGet packages.
4. Build the project.
5. Run the application using **Ctrl+F5**.

**Visual Studio Code**

1. Clone or download this repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory:

```bash
cd MarkerAppearance
```

5. Restore NuGet packages:

```bash
dotnet restore
```

6. Run the project:

```bash
dotnet run
```

7. Open the local URL displayed in the terminal after the application starts.

## Project Structure

`Pages/Index.razor` - Contains the Syncfusion Blazor Chart implementation, chart data model, sample data collection, and the `PointRender` event handler that customizes marker border appearance based on Y-values.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Official documentation for chart events: https://help.syncfusion.com/chart-sdk/blazor/charts/events

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.