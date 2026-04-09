# customize-the-appearance-using-visual-state-manager-in-.net-maui-expander
In this article, we show how to customize the appearance of the .NET MAUI SfExpander using VisualStateManager, focusing on the "Expanded" and "Collapsed" visual states. The sample demonstrates dynamic header styling and icon color changes based on the expander's state, providing a modern and interactive user experience.

To learn more about these features, check out the official user guide:
- [Getting Started with SfExpander](https://help.syncfusion.com/xamarin/expander/getting-started)

## xaml
```
<ContentPage.Resources>
    <Style TargetType="syncfusion:SfExpander">
        <Setter Property="VisualStateManager.VisualStateGroups">
            <VisualStateGroupList>
                <VisualStateGroup>
                    <VisualState Name="Expanded">
                        <VisualState.Setters>
                            <Setter Property="HeaderBackground" Value="#6750A4"/>
                            <Setter Property="HeaderIconColor" Value="#FFFFFF"/>
                        </VisualState.Setters>
                    </VisualState>
                    <VisualState Name="Collapsed">
                        <VisualState.Setters>
                            <Setter Property="HeaderBackground" Value="#141C1B1F"/>
                            <Setter Property="HeaderIconColor" Value="#49454F"/>
                        </VisualState.Setters>
                    </VisualState>
                </VisualStateGroup>
            </VisualStateGroupList>
        </Setter>
    </Style>
</ContentPage.Resources>
```

## Implementation Overview
The sample page contains multiple SfExpander controls, each with custom headers and content. The header icon and text color are bound to the expander's state, updating automatically when expanded or collapsed. The following snippet shows how the header is constructed and how the icon color is bound:

```
<syncfusion:SfExpander x:Name="expander1" HeaderIconPosition="Start" IsExpanded="True">
	<syncfusion:SfExpander.Header>
		<Grid>
			<Grid.RowDefinitions>
				<RowDefinition Height="48"/>
			</Grid.RowDefinitions>
			<Grid.ColumnDefinitions>
				<ColumnDefinition Width="20"/>
				<ColumnDefinition Width="*"/>
			</Grid.ColumnDefinitions>
			<Label Text="&#xe703;" TextColor="{Binding Path=HeaderIconColor,Source={x:Reference expander1}}" FontSize="16" Margin="0,2,0,2"
				   FontFamily='{OnPlatform Android=AccordionFontIcons.ttf#,WinUI=AccordionFontIcons.ttf#AccordionFontIcons,MacCatalyst=AccordionFontIcons,iOS=AccordionFontIcons}'
				   VerticalOptions="Center" VerticalTextAlignment="Center"/>
			<Label CharacterSpacing="0.25" TextColor="{Binding Path=HeaderIconColor,Source={x:Reference expander1}}" FontFamily="Roboto-Regular"  Text="Invoice Date" FontSize="14" Grid.Column="1" VerticalOptions="CenterAndExpand"/>
		</Grid>
	</syncfusion:SfExpander.Header>
	<syncfusion:SfExpander.Content>
		<Grid Padding="18,8,0,18" >
			<Label CharacterSpacing="0.25" FontFamily="Roboto-Regular"  Text="11:03 AM, 15 January 2019" FontSize="14" VerticalOptions="CenterAndExpand"/>
		</Grid>
	</syncfusion:SfExpander.Content>
</syncfusion:SfExpander>
```

## How it works
- **Visual States:** The VisualStateManager allows you to define appearance changes for the SfExpander based on its state. In this sample, the header background and icon color are set differently for "Expanded" and "Collapsed" states.
- **Data Binding:** The header icon and text color are dynamically bound to the expander's state, ensuring seamless UI updates.
- **Multiple Expanders:** The page demonstrates several expanders, each with unique content and icons, all styled using the same visual state logic.
- **Platform-Specific Customization:** The sample uses `OnPlatform` to adjust margins, stroke thickness, and font family for different platforms, ensuring a consistent look and feel across devices.

## Conclusion

By using VisualStateManager with SfExpander in .NET MAUI, you can create visually rich, interactive UI elements that respond to user actions. This approach enables you to deliver a polished experience with dynamic styling and platform-specific adjustments. For more details and advanced scenarios, refer to the [Syncfusion Expander User Guide](https://help.syncfusion.com/xamarin/expander/getting-started).
