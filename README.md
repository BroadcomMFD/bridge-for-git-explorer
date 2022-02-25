# Bridge for Git Explorer <!-- omit in toc -->

<div id="header" align="center">

[![Version](https://vsmarketplacebadge.apphb.com/version-short/broadcomMFD.bridge-for-git-explorer.svg)](https://marketplace.visualstudio.com/items/broadcomMFD.bridge-for-git-explorer/changelog)
[![Downloads](https://vsmarketplacebadge.apphb.com/downloads/broadcomMFD.bridge-for-git-explorer.svg)](https://vsmarketplacebadge.apphb.com/downloads/broadcomMFD.bridge-for-git-explorer.svg)
[![Support](https://img.shields.io/badge/Broadcom-support-red)](https://img.shields.io/badge/Broadcom-support-red)

</div>

Bridge for Git Explorer enables you to work with work-environment Git-Endevor mappings that are synchronized with Endevor using Endevor Bridge for Git. When you work with a work-environment mapping, you may need to add elements from up the Endevor map back to your mapping. Bridge for Git Explorer reads the information about the mapping that you cloned in your VS Code workspace and provides a list of elements from up the map for that particular Endevor inventory location.

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Create Profiles](#create-profiles)
  - [Work with Elements](#work-with-elements)
- [Use Cases](#use-cases)
  - [Add to Mapping](#add-to-mapping)
  - [Add to Mapping with Dependencies](#add-to-mapping-with-dependencies)
- [Environment Variables](#environment-variables)
- [Usage Tips](#usage-tips)
- [Troubleshooting](#troubleshooting)
- [Technical Assistance and Support](#technical-assistance-and-support)

## Prerequisites

Ensure that you meet the following prerequisites before you use Bridge for Git Explorer:

**Host-side prerequisites:**

- Endevor version 18.1 with the following PTFs:

  - SO15978

**Note:** Bridge for Git Explorer only works with v2 of the REST API

- [Endevor Bridge for Git](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/set-up-and-run-the-ca-endevor-bridge-for-git.html)

**Client-side prerequisites:**

- [Endevor plug-in for Zowe CLI version 6.4.0 or higher](https://www.npmjs.com/package/@broadcom/endevor-for-zowe-cli)
- [Endevor Bridge for Git plug-in for Zowe CLI version 2.1.0 or higher](https://www.npmjs.com/package/@broadcom/endevor-bridge-for-git-for-zowe-cli)
- Cloned and opened synchronized Git-Endevor mapping in the VS Code workspace. For more information, see [Access and Clone a Synchronized Repository](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/use-the-ca-enterprise-git-bridge/access-and-clone-an-initialized-git-endevor-mapping.html) in the Broadcom documentation.

## Getting Started

Create an Endevor profile and an EBG profile and review use cases to see how you can use the full potential of Bridge for Git Explorer.

### Create Profiles

The Bridge for Git Explorer extension uses credentials of your Endevor profile to provide you with the list of elements that you can add to your synchronized mapping. Before you can use the extension, ensure that you create two types of profiles: an Endevor profile and an EBG profile.

**Note:** Skip the following procedures if you already have the required profiles.

- Create an Endevor profile.

  1. Use the following command to create an Endevor profile:

     ```shell
     zowe profiles create endevor <profile name> --protocol http(s) --host <hostname> --port <port number> --user <endevor username> --password <endevor pwd>
     ```

  2. Ensure that the profile has the same Endevor configuration that is used for the Git-Endevor mapping in your workspace. For more information about creating an Endevor profile, see [Endevor Plug-in for Zowe CLI](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-brightside/3-0/zowe-cli/available-cli-plug-ins/ca-endevor-scm-plug-in-for-zowe-cli.html) in the Broadcom documentation.

     Alternatively, you can use an API ML base profile. For more information see [Base Profiles](https://docs.zowe.org/stable/user-guide/cli-usingcli/#base-profiles) on Zowe Docs.

- Create an EBG profile with Git credentials.

  1. Use the following command to create an Endevor profile:

     ```shell
     zowe profiles create ebg <profile_name> --protocol http(s) --host <hostname> --port <port number> --user <git_user> --token <personal_access_token>
     ```

  2. Ensure that the profile contains the same information for the Bridge for Git server you used to create the mapping. For more information about creating an Endevor Bridge for Git profile, see [Endevor Bridge for Git Plug-in for Zowe CLI](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/ca-endevor-bridge-for-git-plug-in-for-zowe-cli.html) in the Broadcom documentation.

You now can access your work-environment mapping in your workspace and start to use the extension.

**Note:** If you do not have a profile for the Endevor web services instance that was used to create the synchronized Git-Endevor mapping, the application prompts you to provide your mainframe credentials for that web services instance. The application then creates a session during which you can add elements to your mapping.

### Work with Elements

Expand your Endevor inventory in the tree and proceed to work with the elements.

**Follow these steps:**

1. Click the Bridge for Git Explorer icon in the activity bar.

   The extension opens and the name and branch of your work-environment mapping appear in the tree.

2. Click the name of the mapping to expand the tree.

3. View the available systems, subsystems, and elements of the Endevor inventory location by clicking through the folders in the tree.

4. Click an element to view its contents.

5. (Optional) To see the location details of an element, hover over and right-click the element, and select **View details**.

## Use Cases

Review the following use cases to familiarize yourself with the available features of the extension:

- [Add to mapping](#add-to-mapping): You can add an element from your workstation to the synchronized mapping.
- [Add to mapping with dependencies](#add-to-mapping-with-dependencies): You can add an element with associated files from your workstation to the synchronized mapping.

### Add to Mapping

When you navigate the Endevor map and find the needed element, you can select and add the element to your synchronized mapping. Then you can add the element to your local branch.

**Follow these steps:**

1. Right-click the element you want to add and select **Add to Mapping**.

   You receive a message that your request has been queued.

2. Run the `git pull` command in your terminal to download the element to the local copy of the repository.

   Your element is now available to work with locally.

   **Note:** The retrieval of the element might take some time. Rather than running `git pull` immediately, navigate to your enterprise Git server to check for added elements from the automatic Bridge for Git server synchronization.

![Add to Mapping](images/BFGE-add-to-map.gif?raw=true 'Add to mapping')
<br /><br />

### Add to Mapping with Dependencies

You can select and add an element with associated files to your synchronized mapping.

**Note:** An element can have only up to 50 dependencies.

Right-click an element with dependencies you want to add and select **Add to Mapping With Dependencies**. As well as with the previous option, you can download an element to you cloned repository by issuing the `git pull` command.

For more information about work-environment Git-Endevor mappings, see [Work with Synchronized Repositories](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/use-the-ca-enterprise-git-bridge/work-with-git-endevor-mappings.html).

![Add to Mapping with Dependencies](images/BFGE-add-to-map-dep.gif?raw=true 'Add to mapping with dependencies')
<br /><br />

## Environment Variables

| Name          | Default               | Usage                                                             |
| ------------- | --------------------- | ----------------------------------------------------------------- |
| ZOWE_CLI_HOME | User's home directory | The location of `.zowe` folder for reading ZOWE CLI user profiles |

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

Copyright © 2022 Broadcom. The term "Broadcom" refers to Broadcom Inc. and/or its subsidiaries.
