---
title: layouts
date: 2023-01-02T20:33:28-0700
draft: false
weight: 1
---

# overview
XAML layout system supports automatic resizing of elements, layout panels, and visual states

# implementing responsive layouts with xaml
Achieved by using the appropriate layout properties and panels to reposition, resize, and reflow content fluidly.

## layout properties
### Height & Width
- Set to `Auto` or use star sizing (which is the default)
- To set constraints, set `MinWidth`/`MaxWidth` and `MinHeight`/`MaxHeight`.
- To read value at runtime, use `ActualHeight`/`ActualWidth`

### alignment
- Use `HorizontalAlignment`/`VerticalAlignment`

### visibility
- The `Visibility` enum can be `Visible` or `Collapsed`.
- Replace sections of a UI by revealing one panel and collapsing another.

## layout panels
| Panel control         | Fluid UI support               | Element arrangement                                                                                               | Layering              | Stretch values for hor/ver alignment                             | Child content larger than panel                      |
| --------------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------- | --------------------- | ---------------------------------------------------------------- | ---------------------------------------------------- |
| Canvas                | None                           | Positioned absolutely with Canvas.Top and Canvas.Left                                                             | Yes via Canvas.Zindex | Ignored                                                          | Not clipped; Not constrained                         |
| Grid                  | Yes for resizingchild elements | Rows and columns usingGrid.Row and Grid.Column                                                                    | ?                     | Respected                                                        | Clipped;Constrained                                  |
| RelativePanel         |                                | In relation to edge or center of panel and inrelation to each other. Positioned using variousattached properties. | ?                     | Ignored unless attachedproperties for alignmentcause stretching. | Clipped;Constrained                                  |
| StackPanel            |                                | Stacked in a single line horizontally or vertically                                                               | ?                     | Respected in the directionopposite of the Orientationproperty.   | Clipped;Not constrained(must be manuallyconstrained) |
| VariableSizedWrapGrid |                                | Rows and columns that automatically wrap toa new row/column whenMaximumRowsOrColumns is reached.                  |                       | Ignored                                                          | Clipped;Constrained                                  |

# visual states
Use *visual states* to make significant UI changes based on changes to window size or other changes.
You can define visual states for your UI and apply them when the window width/height crosses a threshold.
You define visual states for screen sizes.
- A `VisualState` defines property values applied to an element when it is in a particular state.
- A `VisualStateManager` groups `VisualStates` and applies the appropriate `VisualState` when conditions are met.
- An `AdaptiveTrigger` sets the threshold.
- Alternatively, `VisualStateManager`.`GoToState` can also be called directly.

## set visual states in code
- Use `VisualStateManager`.`GoToState`.
```xml
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

        <SplitView x:Name="mySplitView" DisplayMode="CompactInline" IsPaneOpen="False" CompactPaneLength="20">
                <!-- SplitView content -->

            <SplitView.Pane>
                <!-- Pane content -->
            </SplitView.Pane>
        </SplitView>
    </Grid>
</Page>
```
```cs
// The WideState visual state is applied…
private void CurrentWindow_SizeChanged(object sender, Windows.UI.Core.WindowSizeChangedEventArgs e)
{
    // …here in the SizeChanged event handler when the window width > 640 effective pixels.
    if (e.Size.Width > 640)
        VisualStateManager.GoToState(this, "WideState", false);
    else
        VisualStateManager.GoToState(this, "DefaultState", false);
}
```
## set visual states in xaml
Since Windows 10, it is easier to define visual states in XAML than code (like above). This example is the same as above:
```xml
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

        <SplitView x:Name="mySplitView" DisplayMode="CompactInline" IsPaneOpen="False" CompactPaneLength="20">
            <!-- SplitView content -->

            <SplitView.Pane>
                <!-- Pane content -->
            </SplitView.Pane>
        </SplitView>
    </Grid>
</Page>
```

## visual states and attached properties
When you set the value for an attached property (but not a regular property), surround the attached property name in parantheses:
```xml
<Setter Target="myTextBox.(RelativePanel.AlignHorizontalCenterWithPanel)" Value="True"/>
```

## [Custom State Triggers](https://learn.microsoft.com/en-us/windows/apps/design/layout/layouts-with-xaml#custom-state-triggers)
Created by extending the StateTrigger class.
