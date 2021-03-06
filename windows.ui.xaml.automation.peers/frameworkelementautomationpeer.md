---
-api-id: T:Windows.UI.Xaml.Automation.Peers.FrameworkElementAutomationPeer
-api-type: winrt class
---

<!-- Class syntax.
public class FrameworkElementAutomationPeer : Windows.UI.Xaml.Automation.Peers.AutomationPeer, Windows.UI.Xaml.Automation.Peers.IFrameworkElementAutomationPeer
-->

# Windows.UI.Xaml.Automation.Peers.FrameworkElementAutomationPeer

## -description
Exposes [FrameworkElement](../windows.ui.xaml/frameworkelement.md) derived types (including all controls) to Microsoft UI Automation.

## -remarks
There is no "ControlAutomationPeer" class. [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) serves as implementation for all basic [Control](../windows.ui.xaml.controls/control.md) class scenarios that involve Microsoft UI Automation. This includes behavior that does not necessarily appear as a public API exposure, such as the practical implementations of many of the **Core** methods from [AutomationPeer](automationpeer.md).

[FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) includes extensive base implementation of peer behavior that other peers can use to report information that comes from owner classes at the [UIElement](../windows.ui.xaml/uielement.md) and [FrameworkElement](../windows.ui.xaml/frameworkelement.md) level. For more info, see the "Base implementation in FrameworkElementAutomationPeer" section of [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4).
<!--Maybe eventually also put this info in the Core methods, because it is overriders that most want to know the specifics of each such behavior whereas general consumers might want big picture or the semi client perspective you get from the non Core descs-->

In addition to the **Core** overrides, [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) has two static utility methods that are useful for getting a peer handle from within control code, or for generating items peers from an item container peer for Microsoft UI Automation support. These are:
+ [CreatePeerForElement](frameworkelementautomationpeer_createpeerforelement.md)
+ [FromElement](frameworkelementautomationpeer_fromelement.md)


If you have a need to define a custom automation peer and can't identify a more derived peer class that pairs up with the control or base class you are deriving the owner class from, you should base your peer on [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md). Even if the owner class isn't necessarily a [FrameworkElement](../windows.ui.xaml/frameworkelement.md), you can't practically derive peers from [AutomationPeer](automationpeer.md) directly because [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) has many overrides that provide the expected behavior for layout, automation and UI interactions. You do need to derive your owner class from [UIElement](../windows.ui.xaml/uielement.md) at least, otherwise there is no way to create the peer on automation tree load with [OnCreateAutomationPeer](../windows.ui.xaml/uielement_oncreateautomationpeer.md).

### **FrameworkElementAutomationPeer** derived classes

[FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) is the parent class for several immediately derived classes that implement peer support for Windows Runtime controls and elements. Some of these peer classes are peers that match control base classes rather than practical controls. For example [ButtonBaseAutomationPeer](buttonbaseautomationpeer.md) exists so that it can define shared peer behavior for several classes that support the practical [Button](../windows.ui.xaml.controls/button.md) classes that derive from [ButtonBase](../windows.ui.xaml.controls.primitives/buttonbase.md). Here is the list of classes that directly derive from [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md):

+ [AppBarAutomationPeer](appbarautomationpeer.md)
+ [ButtonBaseAutomationPeer](buttonbaseautomationpeer.md)
+ [CaptureElementAutomationPeer](captureelementautomationpeer.md)
+ [ComboBoxItemAutomationPeer](comboboxitemautomationpeer.md)
+ [DatePickerAutomationPeer](datepickerautomationpeer.md)
+ [FlipViewItemAutomationPeer](flipviewitemautomationpeer.md)
+ [FlyoutPresenterAutomationPeer](flyoutpresenterautomationpeer.md)
+ [GridViewItemAutomationPeer](gridviewitemautomationpeer.md)
+ [GroupItemAutomationPeer](groupitemautomationpeer.md)
+ [HubAutomationPeer](hubautomationpeer.md)
+ [HubSectionAutomationPeer](hubsectionautomationpeer.md)
+ [ItemsControlAutomationPeer](itemscontrolautomationpeer.md)
+ [ListBoxItemAutomationPeer](listboxitemautomationpeer.md)
+ [ListViewBaseHeaderItemAutomationPeer](listviewbaseheaderitemautomationpeer.md)
+ [ListViewItemAutomationPeer](listviewitemautomationpeer.md)
+ [MediaElementAutomationPeer](mediaelementautomationpeer.md)
+ [MenuFlyoutItemAutomationPeer](menuflyoutitemautomationpeer.md)
+ [PasswordBoxAutomationPeer](passwordboxautomationpeer.md)
+ [ProgressRingAutomationPeer](progressringautomationpeer.md)
+ [RangeBaseAutomationPeer](rangebaseautomationpeer.md)
+ [RichEditBoxAutomationPeer](richeditboxautomationpeer.md)
+ [RichTextBlockAutomationPeer](richtextblockautomationpeer.md)
+ [RichTextBlockOverflowAutomation](richtextblockoverflowautomationpeer.md)
+ [ScrollViewerAutomationPeer](scrollviewerautomationpeer.md)
+ [SearchBoxAutomationPeer](searchboxautomationpeer.md)
+ [SemanticZoomAutomationPeer](semanticzoomautomationpeer.md)
+ [SettingsFlyoutAutomationPeer](settingsflyoutautomationpeer.md)
+ [TextBlockAutomationPeer](textblockautomationpeer.md)
+ [TextBoxAutomationPeer](textboxautomationpeer.md)
+ [ThumbAutomationPeer](thumbautomationpeer.md)
+ [TimePickerAutomationPeer](timepickerautomationpeer.md)
+ [ToggleMenuFlyoutItemAutomationPeer](togglemenuflyoutitemautomationpeer.md)
+ [ToggleSwitchAutomationPeer](toggleswitchautomationpeer.md)


## -examples
This example shows the basic subclass requirements for deriving a peer from [FrameworkElementAutomationPeer](frameworkelementautomationpeer.md) and supporting at least one control pattern. This code is an excerpt from the [XAML accessibility sample](http://go.microsoft.com/fwlink/p/?linkid=238570).

```csharp
        public class MediaContainerAP : FrameworkElementAutomationPeer, IRangeValueProvider, IToggleProvider
        {
            MediaElement _mediaElement;
            FrameworkElement _labeledBy;
// nondefault ctors omitted
            protected override object GetPatternCore(PatternInterface patternInterface)
            {
                if (patternInterface == PatternInterface.RangeValue)
                {
                    return this;
                }
                else if (patternInterface == PatternInterface.Toggle)
                {
                    return this;
                }
                return null;
            }


            protected override AutomationControlType GetAutomationControlTypeCore()
            {
                return AutomationControlType.Group;
            }

            protected override string GetLocalizedControlTypeCore()
            {
                return "Video";
            }

            protected override string GetClassNameCore()
            {
                return "MediaElementContainer";
            }
// pattern implementation omitted ...
        }

```

```vbnet
    Public Class MediaContainerAP
        Inherits FrameworkElementAutomationPeer
        Implements IRangeValueProvider
        Implements IToggleProvider
' nondefault ctors omitted ...

        Protected Overrides Function GetPatternCore(patternInterface__1 As PatternInterface) As Object
            If patternInterface__1 = PatternInterface.RangeValue Then
                Return Me
            ElseIf patternInterface__1 = PatternInterface.Toggle Then
                Return Me
            End If
            Return Nothing
        End Function


        Protected Overrides Function GetAutomationControlTypeCore() As AutomationControlType
            Return AutomationControlType.Group
        End Function
        
        Protected Overrides Function GetLocalizedControlTypeCore() as String
            Return "Video"
        End Function
        
        Protected Overrides Function GetClassNameCore() As String
            Return "MediaElementContainer"
        End Function
' pattern implementation omitted ...
End Class
```

```cpp
// header
        public ref class MediaContainerAP sealed :  Windows::UI::Xaml::Automation::Peers::FrameworkElementAutomationPeer
                                                    ,Windows::UI::Xaml::Automation::Provider::IRangeValueProvider
                                                    ,Windows::UI::Xaml::Automation::Provider::IToggleProvider
        {
// nondefault ctors omitted
        protected: 
            virtual Object^ GetPatternCore(PatternInterface patternInterface) override
            {
                if (patternInterface == PatternInterface::RangeValue)
                {
                    return this;
                }
                else if (patternInterface == PatternInterface::Toggle)
                {
                    return this;
                }
                return nullptr;
            }

        protected:
            virtual  AutomationControlType GetAutomationControlTypeCore() override
            {
                return  AutomationControlType::Group;
            }

        protected:
            virtual Platform::String^ GetLocalizedControlTypeCore() override
            {
                return "Video";
            }
            
        protected:
            virtual Platform::String^ GetClassNameCore() override
            {
                return "MediaElementContainer";
            }
// pattern implementation omitted
```



## -see-also
[FrameworkElement](../windows.ui.xaml/frameworkelement.md), [Custom automation peers](http://msdn.microsoft.com/library/aa8da53b-fe6e-40ac-9f0a-cb09637c87b4), [AutomationPeer](automationpeer.md), [XAML accessibility sample](http://go.microsoft.com/fwlink/p/?linkid=238570)