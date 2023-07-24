# Repository super-res-analysis-tool-installation-docs

In this repository we collect and update a number of documents that detail the analysis toolchain that we use in our laboratory and our publications to analyse super resolution imaging datasets.

The documents are generally focused on conda based installs and use the Python and R programming infrastructure. Specifically, we heavily use the python-microscopy environment (abbreviated as PYME) and related packages.

Our current focus is on "development installs", i.e. installs that use the github sources of key packages and describe the build process on the platforms that we regularly use, i.e. Windows and Mac. In the future we might add descriptions of "one-click-installers" where available. The development installs make it relatively easy to track ongoing development in the main github repos that we use to install bug-fixes, new features etc.

The descriptions are generally tested at the time of writing but may fall behind recent developments (due to updates in conda, Python, R etc) over time. We make an effort to regularly update these documents. If you think you notice issues please use the issue tracker associated with this repository to report problems.

## List of main documents

   - [Installing-PYME-etc-windows](Installing-PYME-etc-windows.md): A rundown of the main install on recent windows platforms (windows 10 and windows 11).
   - [Installing-PYME-etc-macos-intel](Installing-PYME-etc-macos-intel.md): A rundown of the main install on an intel mac
   - [Installing-PYME-etc-macos-ARM64](Installing-PYME-etc-macos-ARM64.md): Some specifics of an install on ARM based macs (M1, M2, ...)
   - [R-conda-install-with-notebooks](r-conda-install-with-notebooks.md): Installation of R with a number of extension modules we frequently use and jupyter notebook support

