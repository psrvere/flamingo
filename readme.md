This projects is a tool to help migrate from BuildConfig to Builds.

It is a work in progress.

# Structure of the project:

- `shipwright` folder contains the codebase for builds
- `origin-tests` folder contains the testdata files for buildconfig. Taken from [here](https://github.com/openshift/origin/tree/main/test/extended/builds) and [here](https://github.com/openshift/origin/tree/main/test/extended/testdata/builds)
- `documentation` folder contains the documentation for buildconfig, builds and Shipwright.
- `extracteddata` folder contains processed data from the testdata files.
    - `kind.md` contains the unique kinds from the testdata files.
    - Each folder has 3 files:
        - `1.raw.md` contains the raw data from the testdata files.
        - `2.examples.md` contains the common examples built using the raw data.
        - `3.mapping.md` contains the mapping of the BufildConfig features to the Builds features.
    - `strategy` folder contains the extracted data from the strategy section of the testdata files.