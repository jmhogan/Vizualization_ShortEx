---
title: iSpy event viewer
---

The iSpy event display platform is used widely for CMS outreach and Open
Data. It does not read [MiniAOD](https://twiki.cern.ch/twiki/bin/view/CMS/MiniAOD)
(or any data tier) files directly, but converts them first into ".ig"
files using an EDAnalyzer. This event display tool has stronger 3D
capabilities (including 3D model exports) and more web-friendly
aesthetics, but gives the user less control over the physics displayed
than Fireworks.

## Accessing iSpy

There are several instances of the iSpy viewer for different purposes.
Some capabilities differ between the sites, but the main difference is
which data files are pre-loaded for viewing.

- Production version: <https://ispy-webgl.web.cern.ch/>
- Development version (useful for CMS analysts): <https://ispy-webgl-dev.web.cern.ch/>
- Open Data Portal version: <https://opendata.cern.ch/visualise/events/cms>
- CMS "Masterclass" version for education:    <https://ispy-webgl-masterclass.web.cern.ch/>. This page in particular is pre-loaded with nice 2-lepton and
    4-lepton events.
- To further confuse things, there is another development version
    which is less stable than the other one: <https://ispy-dev.web.cern.ch>. This
    for now includes some VR tests (see below).

## Using the iSpy controls

The iSpy viewer has a panel of menu buttons across the top of the page,
and a panel of Detector/Physics viewing options down the right-hand-side
of the page. As you hover over each menu button a description will pop
up.

-   Open File: click here for options to upload a local `.ig` file, or
    access pre-loaded files stored on the web.
    [EOS](https://twiki.cern.ch/twiki/bin/view/CMS/EOS)
    access is not supported, since ROOT files cannot be read by iSpy.
-   Reload page (CW circle): this \"refresh\" button starts you over
    from a blank screen, you will need to use \"Open File\" to get your
    events back up.
-   Left/Right arrows: scroll through events in the file
-   Home: return to the blank start screen.
-   Zoom in/out: zoom the current display. This can also be done using
    scroll wheels on a mouse or other trackpad shortcuts.
-   Autorotate (CCW circle): this button starts an automation rotation
    of the event display about the y-axis.
-   YX, YZ, XYZ planes: change the plane of view. Rotation will continue
    if it has been turned on. From any of these starting points you can
    click on the image and drag to rotate the view in any direction.
-   Perspective, Orthographic projections: change the default
    \"projection\" view. The perspective projection is tight in on the
    barrel, while the orthographic projection tends to zoom out.
-   Fullscreen: go to fullscreen or exit fullscreen
-   Settings: in this menu you can **\*change the background to
    white\*** and control other view elements like the axes in the
    bottom-left corner or the logo in the upper-left corner.
    -   Clipping pane controls: for detector views, the x/y/z directions
        each have a blue bar that can be scrolled to change the amount
        of the detector that is shown. For example, the ECAL barrel can
        be reduced to just the upper or lower half-cylinder around the
        beam axis.
-   Statistics: shows information about the 3D rendering
-   About: citations for the iSpy software
-   Print image (camera): **\*save this photo!\***
-   Animation (film reel): turns on/off a very cool animation that
    begins with a collision and then spins through the event display,
    zooming in and out. Nice for outreach computer backgrounds!
-   Import/export: import or export 3D model files

In the Detector and Physics panel you can click on any element to open
or close the drop-down menu. For each individual item you can control:

-   Show: click on/off this detector element. Only the ECAL Barrel is
    shown by default, along with reconstructed hits in the ECAL and
    [HCAL](https://twiki.cern.ch/twiki/bin/view/CMS/HCAL/WebHome),
    and hit chambers in the muon detector.
-   Opacity: scroll from transparent to opaque
-   min_pt (or et, energy, etc): choose the lower momentum/energy
    threshold for displaying the object. **\*Only available for tracks
    and physics objects\***
-   Color: choose a fill/frame color

### Calculating invariant mass

For educational purposes, <kbd>m</kbd>is a keyboard shortcut to display the
invariant mass a selected object or pair of objects.

For example, in the Developer iSpy version, open the
`DoubleElectron_Run2012C_0.ig` file and navigate to the 6th event
(`Events/Run_202016/Event_616963273`). This is a nice Z boson candidate,
decaying to 2 electrons.


To improve visibility of the electrons, open the controls for Tracks and
click off the \"Show\" button. The two remaining tracks point directly
to the ECAL hits and represent the electrons. Hover over one electron
track and click when it turns grey. Hover over the other electron track
and click when it turns grey. You should see both tracks turn grey.
Strike the <kbd>m</kbd> key and the invariant mass will appear!

## Producing an iSpy input file

Any CMS event can be processed to produce an iSpy input file.

1. If you are working in [NanoAOD](https://twiki.cern.ch/twiki/bin/view/CMS/NanoAOD), use the `dasgoclient` tools to find a [RECO](https://twiki.cern.ch/twiki/bin/view/CMS/RECO), [AOD](https://twiki.cern.ch/twiki/bin/view/CMS/AOD), or [MiniAOD](https://twiki.cern.ch/twiki/bin/view/CMS/MiniAOD) file the contains the event(s) you wish to study.
1. Follow the instructions on the [iSpy Analyzers Github](https://github.com/cms-outreach/ispy-analyzers) to create a `.ig` file containing your events. **\*Read the entire README first\*** to understand how the EDAnalyzer functions and which `cmsRun` configuration file is best for your use case.
1. Download the `.ig` file to your local computer and upload it into iSpy using the File menu.

### 3D and VR extras

## 3D file export and view

If you have a scene prepared in the display and want to export it to a
3D file press <kbd>Shift</kbd>+<kbd>E</kbd>. This will export the scene to a glTF (GL
Transmission Format) binary file (with a `.glb` extension). You can
view this file by dragging and dropping it to for example, this viewer
[https://cms3d.web.cern.ch/gltf-test](https://cms3d.web.cern.ch/gltf-test).

## VR test

This works best on a mobile device with a viewer but if you don\'t have
a viewer you can get the idea by opening
[https://ispy-dev.web.cern.ch](https://ispy-dev.web.cern.ch/), on your
phone, wait for it to load, and load an event. Then press the button
that looks like a viewer. At the bottom of the scene (you may have to
scroll down) you will see a "ENTER VR" button. Press it and you will
see the stereo view. The direction of travel of the camera follows your
gaze so that if you look at the event it will appear to be moving closer
towards you.
