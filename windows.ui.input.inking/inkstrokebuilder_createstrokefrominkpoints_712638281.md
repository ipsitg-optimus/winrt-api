---
-api-id: M:Windows.UI.Input.Inking.InkStrokeBuilder.CreateStrokeFromInkPoints(Windows.Foundation.Collections.IIterable{Windows.UI.Input.Inking.InkPoint},Windows.Foundation.Numerics.Matrix3x2)
-api-type: winrt method
---

<!-- Method syntax
public Windows.UI.Input.Inking.InkStroke CreateStrokeFromInkPoints(Windows.Foundation.Collections.IIterable<Windows.UI.Input.Inking.InkPoint> inkPoints, Windows.Foundation.Numerics.Matrix3x2 transform)
-->

# Windows.UI.Input.Inking.InkStrokeBuilder.CreateStrokeFromInkPoints

## -description
Creates a stroke from collection of [InkPoint](inkpoint.md) objects.

> [!NOTE]
> Use [CreateStrokeFromInkPoints](inkstrokebuilder_createstrokefrominkpoints.md) and [SetDefaultDrawingAttributes](inkstrokebuilder_setdefaultdrawingattributes.md) to programmatically build strokes for an [InkPresenter](inkpresenter.md).

## -parameters
### -param inkPoints
The collection of [InkPoint](inkpoint.md) objects.

### -param transform
A 2-D transformation matrix.

## -returns
The ink stroke, including the Bézier curve parameters used for final rendering of the stroke.

## -remarks

## -examples

## -see-also
[Pen and stylus interactions](http://msdn.microsoft.com/library/3da4f2d2-5405-42a1-9ed9-3a87bcd84c43), [Ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620308), [Simple ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620312), [Complex ink sample](http://go.microsoft.com/fwlink/p/?LinkID=620314)