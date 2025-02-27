Back to [Projects List](../../README.md#ProjectsList)

# PRISM Volume Rendering

## Key Investigators

- Simon Drouin, ETS Montreal
- Steve Pieper, Isomics, Cambridge MA, USA
- Andrey Titov, ETS Montreal
- Rafael Palomar, Oslo University Hospital / NTNU, Norway
- Mauro Dominguez
- Samuelle St-Onge, ETS Montreal

# Project Description

The goal of this project is to enable the development of advanced 3D rendering techniques in Slicer. The goal is to facilitate access to GPU shaders and enable GPU-based filtering in Slicer by improving shader access multipass rendering in VTK and Slicer. The [PRISM Module](https://github.com/ETS-vis-interactive/SlicerPRISMRendering) in Slicer will serve as a test environment for the new capabilities.

## Long-term Objective

1. Facilitate the development and debugging of GPU shaders for Slicer (see [this branch](https://gitlab.kitware.com/drouin-simon/vtk/-/tree/volume-shader-readability) of VTK that improves shader readability)
2. Extend the principles introduced in the PRISM module to surface rendering and other types of rendering (Adapt [DisplayableManagers](https://github.com/Slicer/Slicer/tree/main/Modules/Loadable/VolumeRendering/MRMLDM) like in the volume rendering module?)
4. Integrate GPU filters in Slicer and connect them with volume rendering in such a way that filtered volumes do not have to be transfered back to CPU memory before rendering. See work by Kyle Sunderland on VTK GPU image filters (branch [here](https://github.com/Sunderlandkyl/VTK/commits/vtkGPUImageFilter3)).
5. Explore custom rendering to simplify integration with the vtk render process.  Prior work includes:
  * Python scripted Actor/Mappers: https://www.slicer.org/wiki/Slicer3:Python:ScriptedActor
  * SimpleMapper: https://github.com/IbisNeuronav/Ibis/tree/master/IbisVTK/vtkExtensions

## PW37 Objective

1. Finish updating the PRISMRendering module to work with Slicer 5.
2. Enable opening shaders with tags in a text editor while running Slicer
  * Previous efforts by Simon Drouin were made to facilitate shader debugging by leaving tags in the shader code. Code is available in [this branch](https://gitlab.kitware.com/drouin-simon/vtk/-/tree/volume-shader-readability).
  * In vtkShaderProgram class, debug functionality is available by setting the string variable FileNamePrefixForDebugging, which loads a shader from a file before rendering or dumps the shader to a file if doesn't already exists. However, this functionality is private. Mappers should have public functions to enable this debugging mechanism.
4. Generalize the mechanism that allows the VolumeRendering module to store vtkShaderProperties in the display node to obtain the same behavior with the Models module.

## Progress and Next Steps

# Illustrations
<iframe width="560" height="315" src="https://www.youtube.com/embed/8ywNFnkJFEM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Background and References

<!-- If you developed any software, include link to the source code repository. If possible, also add links to sample data, and to any relevant publications. -->
- PRISM Module [GitHub repository](https://github.com/ETS-vis-interactive/SlicerPRISMRendering).
- Incomplete [documentation](https://vtk.org/Wiki/VTK/ProgrammableMultiVolumeRendering) for the Volume Rendering shader used by vtkOpenGLVolumeRaycastMapper
- [Original article](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0193636) about the PRISM framework that served as a basis to develop the PRISM module in Slicer
- Previous project weeks
  - [PW36](https://projectweek.na-mic.org/PW36_2022_Virtual/Projects/PRISMRendering/)
  - [PW35](https://projectweek.na-mic.org/PW35_2021_Virtual/Projects/PRISM_volume_rendering/)
  - [PW30](https://projectweek.na-mic.org/PW30_2019_GranCanaria/Projects/GLSLShaders/)
  - [PW28](https://projectweek.na-mic.org/PW28_2018_GranCanaria/Projects/MultiVolumeRendering/)
