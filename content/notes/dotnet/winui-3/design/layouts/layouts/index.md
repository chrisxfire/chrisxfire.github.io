---
title: notes > dotnet > winui 3 > design > layouts > layouts
date: 2023-01-02T20:33:28-0700
draft: true
---
# Overview
XAML layout system supports automatic resizing of elements, layout panels, and visual states

# Implementing Responsive Layouts with XAML
Achieved by using the appropriate layout properties and panels to reposition, resize, and reflow content fluidly.

## Layout Properties
<u>Height & Width</u>
- Set to `Auto` or use star sizing (which is the default)
- To set constraints, set `MinWidth`/`MaxWidth` and `MinHeight`/`MaxHeight`.
- To read value at runtime, use `ActualHeight`/`ActualWidth`

<u>Alignment</u>
- Use `HorizontalAlignment`/`VerticalAlignment`

<u>Visibility</u>
- The `Visibility` enum can be `Visible` or `Collapsed`.
- Replace sections of a UI by revealing one panel and collapsing another.

## Layout Panels
<table style="width:100%;">
<colgroup>
<col style="width: 22%" />
<col style="width: 10%" />
<col style="width: 26%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Panel</strong></p>
<p><strong>control</strong></p></th>
<th><p><strong>Fluid UI</strong></p>
<p><strong>support</strong></p></th>
<th><strong>Element arrangement</strong></th>
<th><strong>Layering</strong></th>
<th><p><strong>Stretch values for</strong></p>
<p><strong>Hor/Ver alignment</strong></p></th>
<th><p><strong>Child content</strong></p>
<p><strong>larger than panel</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Canvas</td>
<td>None</td>
<td><p>Positioned absolutely with Canvas.Top and</p>
<p>Canvas.Left</p></td>
<td><p>Yes via</p>
<p>Canvas.Zindex</p></td>
<td>Ignored</td>
<td><p>Not clipped;</p>
<p>Not constrained</p></td>
</tr>
<tr class="even">
<td>Grid</td>
<td><p>Yes for resizing</p>
<p>child elements</p></td>
<td><p>Rows and columns using</p>
<p>Grid.Row and Grid.Column</p></td>
<td>?</td>
<td>Respected</td>
<td><p>Clipped;</p>
<p>Constrained</p></td>
</tr>
<tr class="odd">
<td>RelativePanel</td>
<td></td>
<td><p>In relation to edge or center of panel and in</p>
<p>relation to each other. Positioned using various</p>
<p>attached properties.</p></td>
<td>?</td>
<td><p>Ignored unless attached</p>
<p>properties for alignment</p>
<p>cause stretching.</p></td>
<td><p>Clipped;</p>
<p>Constrained</p></td>
</tr>
<tr class="even">
<td>StackPanel</td>
<td></td>
<td>Stacked in a single line horizontally or vertically</td>
<td>?</td>
<td><p>Respected in the direction</p>
<p>opposite of the Orientation</p>
<p>property.</p></td>
<td><p>Clipped;</p>
<p>Not constrained</p>
<p>(must be manually</p>
<p>constrained)</p></td>
</tr>
<tr class="odd">
<td>VariableSizedWrapGrid</td>
<td></td>
<td><p>Rows and columns that automatically wrap to</p>
<p>a new row/column when</p>
<p>MaximumRowsOrColumns is reached.</p></td>
<td></td>
<td>Ignored</td>
<td><p>Clipped;</p>
<p>Constrained</p></td>
</tr>
</tbody>
</table>

# Visual States
Use *visual states* to make significant UI changes based on changes to window size or other changes.
You can define visual states for your UI and apply them when the window width/height crosses a threshold.
You define visual states for screen sizes.
- A `VisualState` defines property values applied to an element when it is in a particular state.
- A `VisualStateManager` groups `VisualStates` and applies the appropriate `VisualState` when conditions are met.
- An `AdaptiveTrigger` sets the threshold.
- Alternatively, `VisualStateManager`.`GoToState` can also be called directly.

## <u>Set Visual States in Code</u>
- Use `VisualStateManager`.`GoToState`.

<Page ...
SizeChanged="CurrentWindow_SizeChanged">
<Grid>
<VisualStateManager.VisualStateGroups>
<VisualStateGroup>
<!-- This is the default visual state. When applied, the values defined in the XAML page are applied. -->
<VisualState x:Name="DefaultState">
<Storyboard>
</Storyboard>
</VisualState>
<!-- This visual state… -->
<VisualState x:Name="WideState">
<Storyboard>
<ObjectAnimationUsingKeyFrames
Storyboard.TargetProperty="SplitView.DisplayMode"
Storyboard.TargetName="mySplitView">
<DiscreteObjectKeyFrame KeyTime="0">
<DiscreteObjectKeyFrame.Value>
<!-- …changes the display mode of the SplitView to Inline… -->
<SplitViewDisplayMode>Inline</SplitViewDisplayMode>
</DiscreteObjectKeyFrame.Value>
</DiscreteObjectKeyFrame>
</ObjectAnimationUsingKeyFrames>
<ObjectAnimationUsingKeyFrames
Storyboard.TargetProperty="SplitView.IsPaneOpen"
Storyboard.TargetName="mySplitView">
<!-- …and opens the pane. -->
<DiscreteObjectKeyFrame KeyTime="0" Value="True"/>
</ObjectAnimationUsingKeyFrames>
</Storyboard>
</VisualState>
</VisualStateGroup>
</VisualStateManager.VisualStateGroups>

<SplitView x:Name="mySplitView" DisplayMode="CompactInline"
IsPaneOpen="False" CompactPaneLength="20">
<!-- SplitView content -->

<SplitView.Pane>
<!-- Pane content -->
</SplitView.Pane>
</SplitView>
</Grid>
</Page>

// The WideState visual state is applied…
private void CurrentWindow_SizeChanged(object sender, Windows.UI.Core.WindowSizeChangedEventArgs e)
{
// …here in the SizeChanged event handler when the window width > 640 effective pixels.
if (e.Size.Width > 640)
VisualStateManager.GoToState(this, "WideState", false);
else
VisualStateManager.GoToState(this, "DefaultState", false);
}

## <u>Set Visual States in XAML</u>
Since Windows 10, it is easier to define visual states in XAML than code (like above). This example is the same as above:
<Page ...>
<Grid>
<!-- VisualStateGroups MUST be attached to the first child of the root for triggers to work automatically. -->
<VisualStateManager.VisualStateGroups>
<VisualStateGroup>
<VisualState>
<VisualState.StateTriggers>
<!-- VisualState to be triggered when the window width is >=640 effective pixels. -->
<AdaptiveTrigger MinWindowWidth="640" />
</VisualState.StateTriggers>

<VisualState.Setters>
<Setter Target="mySplitView.DisplayMode" Value="Inline"/>
<Setter Target="mySplitView.IsPaneOpen" Value="True"/>
</VisualState.Setters>
</VisualState>
</VisualStateGroup>
</VisualStateManager.VisualStateGroups>

<SplitView x:Name="mySplitView" DisplayMode="CompactInline"
IsPaneOpen="False" CompactPaneLength="20">
<!-- SplitView content -->

<SplitView.Pane>
<!-- Pane content -->
</SplitView.Pane>
</SplitView>
</Grid>
</Page>

## <u>Visual States and Attached Properties</u>
When you set the value for an attached property (but not a regular property), surround the attached property name in parantheses:
<Setter Target="myTextBox.(RelativePanel.AlignHorizontalCenterWithPanel)" Value="True"/>

## [Custom State Triggers](https://learn.microsoft.com/en-us/windows/apps/design/layout/layouts-with-xaml#custom-state-triggers)
Created by extending the StateTrigger class.
