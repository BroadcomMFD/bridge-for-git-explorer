# Bridge for Git Explorer <!-- omit in toc -->

<div id="header" align="center">

[![Version](https://img.shields.io/badge/version-0.4.0-brightgreen)](https://marketplace.visualstudio.com/items/broadcomMFD.bridge-for-git-explorer/changelog)
![Downloads](https://img.shields.io/visual-studio-marketplace/d/broadcomMFD.bridge-for-git-explorer)
[![Support](https://img.shields.io/badge/Broadcom-support-red)](https://www.broadcom.com/support)

</div>

Bridge for Git Explorer enables you to work with work-environment Git-Endevor mappings that are synchronized with Endevor using Endevor Bridge for Git. When you work with a work-environment mapping, you may need to add elements from up the Endevor map back to your mapping. Bridge for Git Explorer reads the information about the mapping that you cloned in your VS Code workspace and provides a list of elements from up the map for a specified Endevor inventory location.

The extension includes the following features:

- Add elements to mappings
- Add elements with dependencies to mappings
- See history of changes in elements
- View Bridge for Git mapping activity
- Specify processor groups for elements

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Work with Elements](#work-with-elements)
- [Team Configuration File](#team-configuration-file)
- [Use Cases](#use-cases)
  - [Add to Mapping](#add-to-mapping)
  - [Add to Mapping with Dependencies](#add-to-mapping-with-dependencies)
  - [Show History](#show-history)
  - [Specify Processor Groups for Elements](#specify-processor-groups-for-elements)
  - [Review Mapping Activity](#review-mapping-activity)
- [Usage Tips](#usage-tips)
- [Troubleshooting](#troubleshooting)
- [Technical Assistance and Support](#technical-assistance-and-support)

## Prerequisites

Ensure that you meet the following host-side and client-side software requirements before you use Bridge for Git Explorer:

**Host-side prerequisites:**

- Install either Endevor version 18.0.12 with the SO09580 and SO09581 PTFs or Endevor version 18.1 with the SO15978 PTF.
- Install Endevor Web Services.
- Install [Endevor Bridge for Git](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/installing-ca-endevor-bridge-for-git.html).

**Client-side prerequisites:**

- Install Visual Studio Code.
- Access to either Endevor version 18.0.12 with the SO09580 and SO09581 PTFs or Endevor version 18.1 with the SO15978 PTF.
- Access to Bridge for Git version 2.13 or higher.
- Cloned and opened synchronized Git-Endevor mapping in the VS Code workspace. For more information, see [Access and Clone a Synchronized Repository](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/Using-ca-enterprise-git-bridge/access-and-clone-an-initialized-git-endevor-mapping.html) in the Broadcom documentation.

## Getting Started

Ensure that you have a Git-Endevor mapping in your VS Code workspace to start working with the extension. Review the use cases to see how you can use the full potential of Bridge for Git Explorer.

With the 0.4.0 release, Bridge for Git Explorer introduces the following benefits:

- Improved experience with profiles
- Ability to view the Bridge for Git mapping activity
- Ability to view the history of elements up the map
- Functionality that enables you to specify processor groups for elements

The extension continually supports Zowe V1 profiles and team configuration files that contain your Endevor Connection details and Bridge for Git server credentials. However, you do not need to have these types of profiles to work with the extension. If you do not have Zowe V1 profiles or team configuration files, the extension prompts you to specify missing values. In this scenario, the specified values are stored till the end of the VS Code session only.

**Note:** Credentials from existing Zowe V1 and team configuration files persist between Bridge for Git Explorer sessions.

### Work with Elements

Expand your Endevor inventory in the tree and proceed to work with the elements.

**Follow these steps:**

1. Click the Bridge for Git Explorer icon in the Activity Bar.

   The extension opens and the name and branch of your work-environment mapping are displayed in the tree.

2. Click the name of the mapping to expand the tree.

3. View the available systems, subsystems, and elements of the Endevor inventory location by browsing the folders in the tree.

4. Click an element to view its contents.

5. (Optional) To see the location details of an element, hover over and right-click the element, and select **View details**.

## Team Configuration File

Bridge for Git Explorer supports reading a global team configuration (team config) file. Usually, a system administrator or team leader generates a team config file that contains information about the profiles you need to access certain services, such as Endevor and Bridge for Git. You can use global team configs with your team members to share information about your Endevor connections and Bridge for Git server. For more information about team config, see [Using Team Profiles](https://docs.zowe.org/stable/user-guide/cli-using-using-team-profiles) on Zowe Docs.

As an application developer, you can obtain a shared global configuration file from your system administrator and use the file to access shared systems. As a system administrator, you need to have [Zowe CLI](https://docs.zowe.org/stable/user-guide/cli-installcli) on your workstation before you create a team configuration file.

## Use Cases

Review the following use cases to familiarize yourself with the available features of the extension:

- [Add to mapping](#add-to-mapping): You can add an element from your workstation to the synchronized mapping.
- [Add to mapping with dependencies](#add-to-mapping-with-dependencies): You can add an element with associated files from your workstation to the synchronized mapping.
- [Show history](#show-history): You can view the history of the elements up the map in your mapping.
- [Specify processor groups for elements](#specify-processor-groups-for-elements): You can specify a processor group for an element that you can use for the Generate action.
- [Review Mapping Activity](#review-mapping-activity): Review the events that occur in and the status of your mapping.

### Add to Mapping

When you navigate the Endevor map and find the needed element, you can select and add the element to your synchronized mapping. Then you can download the element to your local branch by pulling the element from you remote repository.

1. Right-click the element you want to add and select **Add to Mapping**.

   You receive a message that your request has been queued.

2. Ensure that your element is added to the repository by checking the status of the mapping in the **Bridge for Git Mapping Activity** section.

   Alternatively, you can check the status of the mapping in the Bridge for Git application.

3. Click the **Source Control** icon in the VS Code Activity Bar.

4. Click the **... (three ellipses)** icon in the **Source Control Repositories** section.

5. Select the **Pull** option to synchronize your remote repository with the local repository.

   Alternatively, you can issue the `git pull` command in your terminal to synchronize the repositories.

   Your element is now available to work with locally.

![Add to Mapping](images/BFGE-add-to-map.gif?raw=true 'Add to mapping')
<br /><br />

### Add to Mapping with Dependencies

You can select and add an element with associated files to your synchronized mapping.

**Note:** An element can have only up to 50 dependencies.

Right-click an element with dependencies you want to add and select **Add to Mapping With Dependencies**.

As well as with the previous option, you can download an element to your cloned repository by pulling the element, using the in-built git VS Code **Pull** option or by issuing the `git pull` command in your terminal.

For more information about work-environment Git-Endevor mappings, see [Work with Synchronized Repositories](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/Using-ca-enterprise-git-bridge/work-with-git-endevor-mappings.html).

![Add to Mapping with Dependencies](images/BFGE-add-to-map-dep.gif?raw=true 'Add to mapping with dependencies')
<br /><br />

### Show History

Review the history of the elements from up the map in your mapping to identify changes and see the authors and dates of changes. The history of changes is displayed in the **Element History** section in the explorer tree.

1. Right-click an element and select the **Show History** option.

   The element is displayed in the editor area. The **Element History** section displays a list of changes.

2. Select an item from the list to display the details.

   The element with highlighted changes is displayed in the editor area.

![Show History](images/BFGE-show-history.gif?raw=true 'Show History')
<br /><br />

### Specify Processor Groups for Elements

Specify a processor group for an element.

1. Open your workspace in VS Code.

2. Right-click an element in the tree and select the **Update Processor Group** option.

   The drop-down menu with processor groups is displayed in the editor area.

3. Select a processor group from the drop-down menu.

   The notification confirming the update is displayed.

4. Push a commit to synchronize the element with your GitHub repository.

![Specify Processor Groups for Elements](images/BFGE-proc-group.gif?raw=true 'Specify Processor Groups for Elements')
<br /><br />

### Review Mapping Activity

The extension enables you to review the Bridge for Git mapping activity that lists events and their respective actions for the currently opened mapping.
The events include mapping initialization, refresh, generate, and deletion.

For example, you can review whether a newly added element is already in your mapping so that you can pull the added element back to your local repository.

1. Add an element to your mapping by using the **Add to Mapping** option.

2. Navigate to the **Bridge for Git Mapping Activity** section.

3. Check the status of the repository.

   If the added element is in the repository already, you can pull the element back to your cloned repository.

## Usage Tips

- **Select multiple elements:** You can select multiple elements and perform actions against the selected elements at once. Press and hold **Ctrl (or ⌘)** + click elements you want to select. You can then right-click one of the selected elements to see available options. To unselect the elements, press **Esc** key.

## Troubleshooting

To identify issues in Bridge for Git Explorer, view specific information related to an error message in the output stream of the extension.

**Follow these steps:**

1. Open a new terminal.
2. Select the **OUTPUT** tab.
3. Select **Bridge for Git Explorer** in the drop-down list at top right corner of the terminal dialog box.

## Technical Assistance and Support

The Bridge for Git Explorer extension is made available to customers on the Visual Studio Code Marketplace in accordance with the terms and conditions contained in the provided End-User License Agreement (EULA).

If you are on active support for Endevor, you get technical assistance and support in accordance with the terms, guidelines, details, and parameters that are located within the Broadcom [Working with Support](https://techdocs.broadcom.com/us/product-content/admin-content/ca-support-policies.html?intcmp=footernav) guide.

This support generally includes:

- Telephone and online access to technical support
- Ability to submit new incidents 24x7x365
- 24x7x365 continuous support for Severity 1 incidents
- 24x7x365 access to Broadcom Support
- Interactive remote diagnostic support

Technical support cases must be submitted to Broadcom in accordance with guidance provided in “Working with Support”.

Note: To receive technical assistance and support, you must remain compliant with “Working with Support”, be current on all applicable licensing and maintenance requirements, and maintain an environment in which all computer hardware, operating systems, and third party software associated with the affected Broadcom software are on the releases and version levels from the manufacturer that Broadcom designates as compatible with the software. Changes you elect to make to your operating environment could detrimentally affect the performance of Broadcom software and Broadcom shall not be responsible for these effects or any resulting degradation in performance of the Broadcom software. Severity 1 cases must be opened via telephone and elevations of lower severity incidents to Severity 1 status must be requested via telephone.

---

Copyright © 2023 Broadcom. The term "Broadcom" refers to Broadcom Inc. and/or its subsidiaries.
