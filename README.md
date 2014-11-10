
# Rackspace Cloud Orchestration API documentation

## Resources

This github repository contains the source files for the following Rackspace Cloud Orchestration API documentation:

* [Cloud Orchestration Getting Started Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-getting-started/content/)
* [Cloud Orchestration Developer Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-devguide/content/)
* [Cloud Orchestration Templates Developer Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-templates-devguide/content/)
* [Cloud Orchestration Release Notes](http://docs.rackspace.com/orchestration/api/v1/orchestration-releasenotes/content/)

## Contributing

Contributions are welcome! To suggest changes to the documentation, submit an [issue](https://github.com/rackerlabs/docs-cloud-orchestration/issues) or [pull request](https://github.com/rackerlabs/docs-cloud-orchestration/pulls).

To make changes to a project, create your own fork of the project and send a pull request to have your changes reviewed and merged into the master branch as appropriate.

### Building from Source

This repository uses Maven to generate the output documentation. Command line users can generate the complete output from this repository by using the following command:

mvn clean generate-sources

The output appears in PDF and HTML form in the following locations. The items in the **Name** column link to the location where the documentation is published, when available.

| Name | Build Location |
| --- | --- |
| [Getting Started Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-getting-started/content/) | target/docbkx/webhelp/orchestration-getting-started-external |
| [Developer Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-devguide/content/) | target/docbkx/webhelp/orchestration-devguide-external |
| [Templates Developer Guide](http://docs.rackspace.com/orchestration/api/v1/orchestration-templates-devguide/content/) | target/docbkx/webhelp/orchestration-templates-devguide-external |
| [Release Notes](http://docs.rackspace.com/orchestration/api/v1/orchestration-releasenotes/content/) | target/docbkx/webhelp/orchestration-releasenotes-external |
| Release Notes (Internal) | target/docbkx/webhelp/orchestration-releasenotes-internal |

#### Editors

You can use any text editor to work with these source files. If you want to use an IDE, consider [NetBeans](http://netbeans.org). This cross-platform IDE offers seamless support for Maven projects and does not require  additional configuration to open the **pom.xml** file as a project. You can configure the project so that the **Build** command, which appears when you right-click a project in the **Projects** pane, executes the `clean generate-sources` command. To do so, perform the following steps:

1. Right-click the project in the **Projects** window and select **Properties**.
2. Select the **Build** category in the left pane, and then select the **Build project** action in the right pane.
3. Change **Execute Goals** to `clean generate-sources`
4. *(Optional)* Repeat steps 2 and 3 for the **Clean and Build project** and **Build with Dependencies** actions.

### Quick Links

The files that are most likely to be of interest are:

* [src/main/resources/orchestration-getting-started.xml](src/main/resources/orchestration-getting-started.xml)
* [src/main/resources/orchestration-devguide.xml](src/main/resources/orchestration-devguide.xml)
* [src/main/resources/orchestration-temlates-devguide.xml](src/main/resources/orchestration-templates-devguide.xml)
* [src/main/resources/wadl/orchestration-api.wadl](wadl/orchestration-api.wadl)

If you want to make changes to the example files referenced in the WADL file, you can find the example files at [wadl/samples](wadl/samples).

The status codes referenced by the WADL files are defined in the wadl at [wadl/orchestration-api.wadl](wadl/orchestration-api.wadl).
