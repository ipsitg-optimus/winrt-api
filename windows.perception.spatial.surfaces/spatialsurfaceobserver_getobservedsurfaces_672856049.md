---
-api-id: M:Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver.GetObservedSurfaces
-api-type: winrt method
---

<!-- Method syntax
public Windows.Foundation.Collections.IMapView<System.Guid, Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo> GetObservedSurfaces()
-->

# Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver.GetObservedSurfaces

## -description
Gets metadata for the set of surfaces observed within the bounding volume at the moment.

## -returns
The observed surfaces.

## -remarks
Each SpatialSurfaceInfo snapshot is immutable, so you can compare their values later to see if a given surface has recently experienced a mesh update.

Correlating the Id and UpdateTime properties across multiple observations lets you identify new mesh, updated mesh and removed mesh:

If you see a SpatialSurfaceInfo with an Id you haven't seen before, treat it as new mesh.

If you see a SpatialSurfaceInfo with a known Id, but with a new UpdateTime, treat it as updated mesh.

If you no longer see a SpatialSurfaceInfo with a known Id, treat it as removed mesh.

## -examples

## -see-also
