java-example-client-data-io
===========================

The following tutorials demonstrate how different types of data inputs and outputs can be sent to and retrieved from [DeployR-managed](http://deployr.revolutionanalytics.com) R sessions when executing R code or R scripts using the [DeployR client library](http://deployr.revolutionanalytics.com/dev).

- [About: DeployR Inputs](#about-deployr-inputs)
- [About: DeployR Outputs](#about-deployr-outputs)
- [Tutorial: Authenticated Users & Data I/O](#tutorial-authenticated-users--data-io)
- [Tutorial: Anonymous Users & Data I/O](#tutorial-anonymous-users--data-io)
- [Tutorial: All Users Big Data I/O](#tutorial-all-users-big-data-io)
- [Tutorial: R Analytics Example Dependencies](#r-analytics-example-dependencies)
- [License](#license)


### About: DeployR Inputs

DeployR supports the following types of data inputs:

1. [DeployR-encoded](http://deployr.revolutionanalytics.com/documents/dev/clientlib/#encoding) application generated data, including data read from databases, data input by end-users, or data otherwise derived by your application logic. These data can be sent as inputs and automatically decoded into the workspace of an R session when executing R code or an R script.

2. References to external data sources, including URLs, external Web service endpoints or database connection endpoints along with associated credentials and/or record identifiers. These data can be sent as DeployR-encoded inputs and automatically decoded into the workspace and then used to load data directly into an R session when executing R code or an R script.

3. Uploaded data from files on the local file system (disk). 

4. References to repository-managed binary data files (rData) that cause the corresponding file data to be loaded into the workspace of an R session when executing R code or an R script.

5. References to repository-managed data files (csv, dat, xls, etc) that cause the corresponding file data to be loaded into the working directory of an R session when executing R code or an R script.


### About: DeployR Outputs

DeployR supports the following types of data outputs:

1. [DeployR-encoded](http://deployr.revolutionanalytics.com/documents/dev/clientlib/#encoding) R object workspace data (data.frame, list, primitive, etc) that were generated by the execution of R code or an R script.

2. References to R session working directory binary files (rData, png, jpg, etc) that were generated by the execution of R code or an R script. These binary files can be downloaded from DeployR on request.

3. References to R session working directory data files (csv, dat, xls, etc) that were generated by the execution of R code or an R script. These data files can be downloaded from DeployR on request.

4. References to R session graphics device plots (png, jpg, svg, etc) that were generated by the execution of R code or an R script. These plots can be downloaded from DeployR on request.

5. References to repository-managed data or binary files that were stored following the execution of R code or an R script. These repository-managed files can be downloaded from DeployR on request.


## Tutorial: Authenticated Users & Data I/O

Authenticated (trusted) users can execute both R code and repository-managed R scripts that they themselves have created or R scripts that have been shared by other authenticated (trusted) users.

Authenticated users can use the full set of data inputs and outputs described above.

The following tutorials demonstrate the data I/O options available to authenticated users:

- [Discrete Execution Data I/O](examples/tutorial/auth-discrete-exec)
- [Stateful Execution Data I/O](examples/tutorial/auth-stateful-exec)
- [Stateful Preload & Execution Data I/O](examples/tutorial/auth-stateful-preload)

## Tutorial: Anonymous Users & Data I/O

Anonymous (untrusted) users can only execute repository-managed R scripts that have been assigned _public_ access privileges by authenticated (trusted) users.

Anonymous users can use the full set of data inputs and outputs described above with a single exception: anonymous users can not cause data or binary files to be stored into the DeployR-repository and as such can not retrieve references to repository-managed data or binary files following an execution.

The following tutorial demonstrate the data I/O options available to anonymous users:

- [Discrete Execution Data I/O](examples/tutorial/anon-discrete-exec)

## Tutorial: All Users Big Data I/O

The set of data I/O tutorials detailed above for authenticated and anonymous users cover most use cases for moving data into and out of the DeployR server. However, there are times when you may want to work with data that is simply too large to move between your client application and the DeployR server. This is particularly true when you are working with genuinely `Big Data` files.

For this, DeployR provides support for a feature called the External (Big Data) Directories. See [here](http://deployr.revolutionanalytics.com/documents/admin/bigdata/) for details.


## R Analytics Example Dependencies

```
Source: analytics/*
```

Most of the examples use a sample data file based on the Hipparcos Star
Dataset, found [here](http://astrostatistics.psu.edu/datasets/HIP_star.html).

This data file is found here:

```
analytics/hipStar.dat
```

Some of the examples use a sample binary file containing an R data.frame based
on the Hipparcos Star Dataset, found [here](http://astrostatistics.psu.edu/datasets/HIP_star.html).

This binary file is found here:

```
analytics/hipStar.rData
```

All of the examples use a sample R script that demonstrates the handling of inputs and the generation of outputs each time the script is executed.

This R script is found here:

```
analytics/dataIO.R
```

The R scripts and data files used by these example application are
*not bundled* by default within the DeployR 7.4 repository.

The simplest way to deploy these files for use when running these
example applications is to use the [DeployR CLI](https://github.com/microsoft/cli).
The CLI will automatically deploy the file dependencies to the DeployR
repository before running the examples.

If for any reason you want to manually deploy these files for testing
purposes you can use the DeployR Repository Manager as follows:

1. Log in as testuser into the [Repository Manager](http://deployr.revolutionanalytics.com/documents/help/repo-man/)
2. Create a new repository directory called `example-data-io`
3. Upload `analytics/hipStar.dat` to the `example-data-io`
   directory and set the access control to `public`.
4. Upload `analytics/hipStar.rData` to the `example-data-io directory`
   directory and set the access control to `public`.
5. Upload `analytics/dataIO.R` to the `example-data-io` directory
   directory and set the access control to 1public`.


## License ##

Copyright (C) 2010-2016, Microsoft Corporation

This program is licensed to you under the terms of Version 2.0 of the
Apache License. This program is distributed WITHOUT
ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING THOSE OF NON-INFRINGEMENT,
MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. Please refer to the
Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0) for more 
details.
