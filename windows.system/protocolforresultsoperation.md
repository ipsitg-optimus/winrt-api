---
-api-id: T:Windows.System.ProtocolForResultsOperation
-api-type: winrt class
---

<!-- Class syntax.
public class ProtocolForResultsOperation : Windows.System.IProtocolForResultsOperation
-->

# Windows.System.ProtocolForResultsOperation

## -description
Represents the result to the application that launched the current application for results.

## -remarks
Use this class from an activated application launched via [Launcher.LaunchUriForResultsAndContinueAsync](launcher_launchuriforresultsandcontinueasync.md) to indicate when activation is complete and to return a result to the activating application. This class is passed to the activated application's [Application.OnActivated](../windows.ui.xaml/application_onactivated.md) () method via the [IActivatedEventArgs ](../windows.applicationmodel.activation/iactivatedeventargs.md) argument.

## -examples

## -see-also
