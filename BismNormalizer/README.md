# BismNormalizer

### General Usage

Download from the BISM Normalizer [Visual Studio Marketplace page](https://marketplace.visualstudio.com/items?itemName=ChristianWade.BISMNormalizer3). New releases will be uploaded to this page.

#### Instructional Videos
1. [Use Cases & Demo](http://www.youtube.com/watch?v=LZdOwfJqFrM)
1. [Object Model & Build Process](http://www.youtube.com/watch?v=r3eGK-dSYuw)
   - Shows the internals of BISM Normalizer 3. Everything still applies except obfuscation, which has been removed.

#### Command to Perform a Release Build

Output goes to bin\ReleaseObfusc

`msbuild BismNormalizer.csproj /verbosity:m /target:Rebuild /property:Configuration=Release`

#### Set Up New Development Machine

Built in VS 2017. Workloads installed must include .NET desktop development and VS extension development.

**NOTE:** May need to temporarily comment out `Import Project="..\packages\MSBuild.Extension.Pack.1.8.0\build\net40\MSBuild.Extension.Pack.targets"` at the bottom of BismNormalizer.csproj to load project into VS for 1st time. After 1st successful load, add it back.

#### Notes & Updates
Update: 4/23/2018: AMO libraries are now accessed through NuGet references, so no longer necessary to install AMO client libraries from the [MSI](https://docs.microsoft.com/en-us/azure/analysis-services/analysis-services-data-providers).

Do a Release build from the command-line to set up cross project references for the 1st time (see command above). The automated tests refer to a localhost SSAS tabular server.

Set BismNormalizer as startup project, and in project properities > Debug tab, set

* Start External Program (assuming Enterprise edition): C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
* Command Line Arguments: /rootsuffix Exp

# ALM Toolkit

ALM Toolkit is the BismNormalizer for PowerBI datasets. It allows for metadata changes without a full refresh of a dataset.

## Getting Started
1. In order to use ALM toolkit, you must have PowerBI admin rights.
1. Find your api address
   * It will be something like `powerbi//api.powerbi.com/v1.0/[Insert Org]/[Insert Workspace]`
1. [High Level Overview](http://alm-toolkit.com/HowToUse)
1. [Detailed Documentation](https://github.com/microsoft/Analysis-Services/blob/master/BismNormalizer/Model%20Comparison%20and%20Merging%20for%20Analysis%20Services.pdf)
