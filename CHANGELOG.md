# Release Notes

### v0.23.2
* Consolidated debug traces to use TF_DEBUG, see developers documentation for available flags.

### v0.23.1
* Bug Fix: Maya 2016 build.

### v0.22.1
* Bug Fix: Fixed playblast issue that caused drift in caches when using animated film offsets on the camera

### v0.22.0
* Bug Fix: Fixed crash in prim resync command when passed an invalid prim path
* Removed unused pxr directory
* Bug Fix: Schemas generation
* Bug Fix: the maya reference update code was double-loading references when switching paths.

### v0.21.0
* Removed legacy TRA Array attributes from the proxy shape
* Bug Fix: Fixed issue that could cause translator plugins to be uninitialised when proxy shape was first created
* Updated to USD 0.8.0
* Various cmake/build improvements

### v0.20.1
* Improvements to colour set export on mesh geometry
* Bug Fix: Force parallel evaluation when running unit tests
* Removed unused asset resolver config
* Bug Fix: Improve selection between maya geometry and usd geometry

### v0.20.0
* Hooked up display Guides + displayRenderGuides attributes to usdImaging
* Added MEL command to provide a simple selection mechanism in USD imaging layer
* Reduced the number of times the translators were being initialized to once per proxy shape instance. 
* Added ability for the translators to say they support an inactive state (so nodes don't get deleted)
* Added reference counting for kRequired transforms. 
* Bug Fix: If a prim changed type as a result of a variant switch, the type info was not updated in the translator context
* Bug Fix: Shapes, Transforms, and DG nodes now correctly deleted (without leaving transforms)
* Bug Fix: Fixed issue where we could end up with invalid transform references in some very rare edge cases
* Bug Fix: Fixed issue where invalid MObjects could be generated within transform reference generation. 
* Bug Fix: Switching from a plugin prim type, to an ignored cache prim, could leave transforms in the scene
* Added the AL_usdmaya_ProxyShapeSelect command to select prims via a command (supports undo/redo). 
* Promoted the CameraTranslator to a properly implemented translator plugin

### v0.19.0
* Added Open Source Licencing
* Documentation Refactor
* Addded End-to-End Tutorial
* Added MayaReference and HostDrivenTransformInfo schema (_the opensource repository is now deprecated_)
* Added MayaReference translator (_the opensource repository is now deprecated_)

### v0.18.1
**Change Log**
* Bug Fix: Fixed issue with custom transform types not being correctly serialised on file Save
* Bug Fix: Fixed issue with transforms with identical names not being correctly deserialised
* Added support for the Intel F16C half-float conversion intrinsics

### v0.18.0
**Change Log**
* AL_usdmaya_LayerCurrentEditTarget command can now take a layer identifier to specify the target layer
* New command AL_usdmaya_LayerCreateLayer added 
* Updated docker config
* Bug Fix: Unchecked pointer access in SchemaNodeRefDB::removeEntries
* proxyShapeImport GUI now displays all usd file types
* Bug Fix: Colour sets now correctly applied on import
* Bug Fix: Maya 2018 compatibility changes

### v0.17.0
**Change Log**
* Built against usd-0.7.5
* Switching StageData to use a UsdStageWeakPtr to avoid keeping some stages alive forever.
* Copy the edit target instead and re-use it when setting it back.
* Add CHANGELOG.md
* Bug Fix: Fixes to make the unit tests run in mayabatch mode.
* Bug Fix: Use shared_ptr to manage driven transform data life time. [#263]
* Bug Fix: Fixing a possible crash with the curve importer.
* Bug Fix: Avoiding a crash when importing a camera.

### v0.16.9
**Change Log**
* Bug Fix: Previous selection crash-fix, that re-parented custom transforms under a temporary, would cause a change in the 
           selection list, which resulted in a crash. 
* Bug Fix: Fixed crash in removeUsdTransforms as a result of Maya deleting the parent of a custom transform
* Bug Fix: Hydra selection highlighting was being overwritten when performing Shift+Select
* The proxy shape now responds to changes of the Active state of plugin translator prims
* Maya 2016 now supported
 
### v0.16.8
**Change Log**
* Bug Fix: fixing a regression that would cause the transform hierarchy to be incorrect
 
### v0.16.7
**Change Log**
* Changes to the driven transforms on the proxy shape
* Ported from CPP unit to googletest, and moved all tests into a test plugin.
* Code now compiles against Maya 2018 beta77
* Bug Fix: session layer handle was incorrectly being wiped after a file load, which could cause a crash
* Bug Fix: Layer::getSubLayers would fail after the scene was reloaded. 
* Bug Fix: Incorrectly warned of storable message attributes
* Bug Fix: Unitialised layer handles could cause a crash
* Bug Fix: Deleting AL_usdmaya_Transform nodes would cause parent transforms to be deleted. 
* Bug Fix: Layer::getParentLayer returning invalid value
* Bug Fix: getAttr "layerNode.framePrecision" now works as expected
* Bug Fix: Chaning the USD edit target now correctly updates the 'hasBeenEditTarget' flag
* Bug Fix: Animated Shear 
* Bug Fix: AL_usdmaya_TransformationMatrix::getTimeCode now correctly returns the animated time values
* Bug Fix: AL_usdmaya_TransformationMatrix::enablePushToPrim would incorrectly create a scalePivot transformation op
* Bug Fix: AL_usdmaya_TransformationMatrix could fail to update if frame 0 was the first animation frame in a sequence. 
* Bug Fix: Selecting a parent of a selected transform, would cause a crash in Maya. 

### v0.16.6
**Change Log**
* Bug Fix: Matrix driven transform node could write an invalid key into the session layer, nuking animation cache data. 
* Bug Fix: Excluded geometry became visible on reload. 
* Bug Fix: Removed option box from Import Proxy Shape (was causing a crash).
* Improvement: Proxy Shape now runs the post-load process immediately, rather than waiting on a defferred MEL call. 

### v0.16.5
**Change Log**
* Ability to set Edit Targets with a map function
* Bug Fix: Edit Targets not correctly preserved during selection changes
* Bug Fix: Export command strips namespaces to avoid crash
* Bug Fix: Camera transforms now correctly animate
* readFromTimeline attribute added to AL_usdmaya_Transform to control when transforms display custom or animated values.

### v0.16.4
**Change Log**
* Bug Fix: playblasts were coming out black
* Bug Fix: OpenGL state not preserved in VP1

### v0.16.3
**Change Log**
* Bug Fix: excluded objects not hidden after file load
* Bug Fix: Prevented crash within draw override. 

### v0.16.2
**Change Log**
* Bug Fix: excluded objects not hidden after variant switch

### v0.16.1
**Change Log**
* Bug Fix: Fixed incorrect depth settings when rendering in Hydra
* Bug Fix: Fixed complexity issue that caused warnings to be spammed into the command prompt. 

### v0.16.0
**Change Log**
* Switched code over to use UsdImaging rather than UsdMayaGL library
* Updated USD base to 0.7.4
* Selection highlighting now visible in the maya viewport. 

### v0.12.1
**Change Log**
* Variant Switching now supported
* Minor Menu GUI improvements
* Dead code removal
* open sourcing prep work, and documentation

### v0.9.14
**Change Log**
*Updated to support ALMayaReferences

**Known Issues**
*Having objects that have a MayaReference to the same path on disk has been reported to cause problems.

### v0.9.13
**Change Log**
*Disabled Asset Resolver Configuration

### v0.9.12
**Change Log**
* "add AL_USDMaya library to python bindings linked libraries"
* Importing of animated attributes

### v0.9.10
**Change Log**
* Updated the AL/__init__.py to merge in with the existing AL module to avoid  UsdMaya from stomping on PythongLibs' AL module.

### v0.9.8
**Change Log**
* Bug Fix: Scenes no longer crash in parallel evaluation mode. http://github.al.com.au/rnd/usdMaya/issues/41
* Bug Fix: Maya no longer crashes when modifying the filepath attribute of a proxyshape node. http://github.al.com.au/rnd/usdMaya/issues/121
* Bug Fix: Frame range incorrectly set when opening a shot. http://github.al.com.au/rnd/usdMaya/issues/72
* Bug Fix: maya crash if rig ref missing. http://github.al.com.au/rnd/usdMaya/issues/84
* Massive rename of nodes, and commands. The previous names (e.g. alUsdProxyShape) have been standardised with the rest of AL, so now it's 'AL_usdmaya_ProxyShape'.
* Support for the export of animated cameras via the 'AL usdmaya Export' translator
* The AL usdmaya plugin has been divorced from the orignal PXR maya plugin
* Remaining python code has been moved, previously you had to import the module by 'from pxrUsd import UsdMaya', now you should use 'from AL import UsdMaya'. 

**Known issues**
* Missing usdImport and usdExport command for animated data - http://github.al.com.au/rnd/usdMaya/issues/108
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k

### v0.9.6
**Change Log**
* Prim->MayaPath: Prim's that translate into a corresponding maya shape now point to the transform above the shape instead of ths shape
* Enabled backface culling in the proxyshapeUi
* Fixed "picaso" bug

**Known issues**
* Missing usdImport and usdExport command for animated data - http://github.al.com.au/rnd/usdMaya/issues/108
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k
* DG Parallel Eval: http://github.al.com.au/rnd/usdMaya/issues/41
* Frame Range http://github.al.com.au/rnd/usdMaya/issues/72
* Crash if ref rig missing http://github.al.com.au/rnd/usdMaya/issues/84

### v0.9.5
**Change Log**
* Simple profiler
* Global Command Executor problems
* Removed pixar mayaUsd source that isn't being used

**Known issues**
* Missing usdImport and usdExport command for animated data - http://github.al.com.au/rnd/usdMaya/issues/108
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k
* DG Parallel Eval: http://github.al.com.au/rnd/usdMaya/issues/41
* Frame Range http://github.al.com.au/rnd/usdMaya/issues/72
* Crash if ref rig missing http://github.al.com.au/rnd/usdMaya/issues/84

### v0.9.4
**Change Log**
* New patch for Maya PR71

**Known issues**
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k
* DG Parallel Eval: http://github.al.com.au/rnd/usdMaya/issues/41
* Frame Range http://github.al.com.au/rnd/usdMaya/issues/72
* Crash if ref rig missing http://github.al.com.au/rnd/usdMaya/issues/84

### v0.9.3
**Change Log**
* Added all_tests target which will be the target ran by the usdMaya_BUILD jenkins job.
* BugFix: Fixed MayaCache: http://github.al.com.au/rnd/usdMaya/issues/37

**Known issues**
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k
* DG Parallel Eval: http://github.al.com.au/rnd/usdMaya/issues/41
* Frame Range http://github.al.com.au/rnd/usdMaya/issues/72
* Crash if ref rig missing http://github.al.com.au/rnd/usdMaya/issues/84

### v0.9.2
**Documentation**
http://github.al.com.au/rnd/usdMaya/wiki

**Change Log**
* Initial UsdMaya unit tests.
* Fix for rabbit vertex windings, rabbit now shows correctly as white.
* Fix for UsdPrim->usdMaya path.
* Fix for crash when burnin can't find parent path.
* Fix for multiple rabbits, now correctly shows one rabbit

**Known issues**
* TLS Problem in maya 2017 - you may have to switch off other plugins when working with our USD Plugin. See https://groups.google.com/forum/#!topic/usd-interest/wJr8c_iTO7k
* MayaCache: http://github.al.com.au/rnd/usdMaya/issues/37
* DG Parallel Eval: http://github.al.com.au/rnd/usdMaya/issues/41
* Frame Range http://github.al.com.au/rnd/usdMaya/issues/72
* Crash if ref rig missing http://github.al.com.au/rnd/usdMaya/issues/84


