# Bridge for Git Explorer <!-- omit in toc -->

<div id="header" align="center">

[![Version](https://img.shields.io/badge/version-0.6.0-brightgreen)](https://marketplace.visualstudio.com/items/broadcomMFD.bridge-for-git-explorer/changelog)
[![Installs](https://img.shields.io/badge/installs-1.9k+-blue)](https://marketplace.visualstudio.com/items/broadcomMFD.bridge-for-git-explorer)
[![Support](https://img.shields.io/badge/Broadcom-support-red)](https://www.broadcom.com/support)

</div>

Bridge for Git Explorer enables you to work with work-environment Git-Endevor mappings that are synchronized with Endevor using Endevor Bridge for Git (BFG). When you work with a work-environment mapping, you may need to add elements from up the Endevor map back to your mapping. Bridge for Git Explorer reads the information about the mapping that you cloned in your VS Code workspace and provides a list of elements from up the map for a specified Endevor inventory location.

The extension enables developers working with Bridge for Git mappings to:

- Configure the pre-push hook
- Add elements to their mapping
- Add elements with dependencies to their mapping
- See the history of changes to elements
- View the activity of their mapping
- Specify processor groups for elements in their mapping

## Table of Contents

- [Announcements and News](#announcements-and-news)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [(Optional) Use Team Config to Manage Profiles](#optional-use-team-config-to-manage-profiles)
  - [Work with Elements](#work-with-elements)
- [Use Cases](#use-cases)
  - [Configure the Pre-push Hook](#configure-the-pre-push-hook)
  - [Add to Mapping](#add-to-mapping)
  - [Add to Mapping with Dependencies](#add-to-mapping-with-dependencies)
  - [Show History](#show-history)
  - [Specify Processor Groups for Elements](#specify-processor-groups-for-elements)
  - [Review Mapping Activity](#review-mapping-activity)
- [Usage Tips](#usage-tips)
- [Troubleshooting](#troubleshooting)
- [Technical Assistance and Support](#technical-assistance-and-support)

## Announcements and News

> Bridge for Git Explorer 0.6.0 is the last version of a standalone extension that will be deprecated soon. You will be able to use all functionality of the extension as part of the [Explorer for Endevor](https://marketplace.visualstudio.com/items?itemName=broadcomMFD.explorer-for-endevor) 2.0 features (yet to be released).

- Version 0.6.0 the extension is compatible with Bridge for Git 3.0. For more information, see [Bridge for Git documentation](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0.html) on TechDocs.
- Added Bridge for Git aliases support. Aliases are useful when you have multiple branches that are mapped to differently named systems or subsystems that point to the same inventory up the map. For more information, see the _Use Aliases for Multi-branching_ section in the [Create and Initialize a Git-Endevor Mapping](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/administrating/mapping-administration/create-and-initialize-a-git-endevor-mapping.html) article on TechDocs.
- Zowe CLI V1 profile support was removed. Instead you can use Zowe V2 and V3-based team configuration (team config) files to store your Bridge for Git and Endevor credentials. Zowe V2 and V3-based team configs are the optional feature and are not required for the extension to work.
- Mapping activity operations limit setting is added. You can now set a limit to the number of mapping activity operations. The default value is 100. For more information, see [Review Mapping Activity](#review-mapping-activity).

## Prerequisites

Ensure that you meet the following host-side and client-side software requirements before you use Bridge for Git Explorer:

**Host-side prerequisites:**

- Install either Endevor version 18.0.12 with the SO09580 and SO09581 PTFs or Endevor version 18.1 with the SO15978 PTF.
- Install Endevor Web Services.
- Install [Endevor Bridge for Git](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/installing.html).

**Client-side prerequisites:**

- Install Visual Studio Code 1.82 or higher.
- Access to either Endevor version 18.0.12 with the SO09580 and SO09581 PTFs or Endevor version 18.1 with the SO15978 PTF.
- Access to Bridge for Git version 2.13 or higher.

## Getting Started

Before you can work with the extension, ensure that you meet the following prerequisites:

1. Create at least one Git-Endevor mapping. For more information, see [Access and Clone a Git-Endevor Mapping](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/using/access-and-clone-an-initialized-git-endevor-mapping.html) on TechDocs.

2. Prepare the following credentials per mapping:

   **Endevor connection:**

   - Mainframe userid and password

   **Endevor Bridge for Git:**

   - Your git server user name and Personal Access Token (PAT)

     For more information on how to obtain a PAT, see the _Personal Access Tokens_ section in [Authentication Methods](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/installing/set-up-git-server-communication/authentication-methods.html) on TechDocs.

To start working with the extension, open your Git-Endevor mapping(s) in your VS Code workspace.

1. Open available Git-Endevor mapping(s) using VSC.

   You should see your branches in the Bridge for Git Explorer view of the extension (the section that is next to the default Activity Bar position).

2. Click the branch to expand your synchronized Endevor inventory location.

   You are prompted to enter your Endevor connection credentials.

   **Notes:**

   - When necessary, you are prompted for your Endevor connection and Endevor Bridge for Git (EBG) credentials.

   - (Optional) If you store Endevor connection and EBG credentials in Zowe team config, VSC persists these credentials for every active session.

   - Endevor connection credentials enable you to expand branches in the Bridge for Git Explorer view, and EBG credentials enable the majority of features (functionalities).

You can now work with your mapping.

Review the [use cases](#use-cases) to see how you can use the full potential of Bridge for Git Explorer.

### (Optional) Use Team Config to Manage Profiles

You can pre-define your Endevor connection access information in Zowe V2 and Zowe V3 team configuration (team config) files. Credentials and profile details from team config files persist between Bridge for Git Explorer sessions.

In the context of team config, "profiles" are a set of properties (like `host`, `port`, `user`, etc.. ) that Endevor connection and Bridge for Git include.

**Tip:** Team config enables team leaders to share multiple Endevor connection and EGB profiles to use Git-Endevor mappings across development teams.

To modify your team `zowe.config.json` file, navigate to the `.zowe` folder in your user home directory. Ensure that you edit the team config, using your Endevor connection and BFG details.

For more information on how to store profiles in a team config file, see [Editing Team Configurations](https://docs.zowe.org/stable/user-guide/cli-using-editing-team-configuration) on Zowe Docs.

**Note:** You might need to request the user information from the team leader that maintains BFG in your organization.

**Example: EBG profile in a `zowe.config.json` file**

```json
"$schema": "./zowe.schema.json",
"profiles": {
  "bfg_profile_name": {
     "type": "ebg",
     "properties": {
        "protocol": "https",
        "host": "your.host.net",
        "port": 8080,
        "user": "username",
        "token": ""
     },
     "secure": []
  }
}
```

where

- `bfg` is the name of your Bridge for Git profile.

  **Note:** Ensure that `host` and `port` match the `host` and `port` that are specified in the `url` of your `mapping.json` in the `.ebg` folder.

- `token` is a PAT for your Enterprise git server.

  For more information, see [Authentication Methods](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/installing/set-up-git-server-communication/authentication-methods.html) on TechDocs.

**Example: Endevor connection in a `zowe.config.json` file**

```json
"$schema": "./zowe.schema.json",
"profiles": {
  "endevor_connection_name": {
     "type": "endevor",
     "properties": {
        "host": "your.host.net",
        "port": 8080,
        "protocol": "https",
        "basePath": "/WebService/api/v2/",
        "user": "username",
        "password": "password",
        "rejectUnauthorized": false
     },
     "secure": []
  }
}
```

### Work with Elements

Expand your Endevor inventory in the tree and proceed to work with the elements.

1. Click the Bridge for Git Explorer icon in the Activity Bar.

   The extension opens and the name and branch of your work-environment mapping are displayed in the tree.

2. Click the name of the mapping to expand the tree.

3. View the available systems, subsystems, and elements of the Endevor inventory location by browsing the folders in the tree.

4. Click an element to view its contents.

5. (Optional) To see the location details of an element, hover over and right-click the element, and select **View details**.

## Use Cases

Review the following use cases to familiarize yourself with the available features of the extension:

- [Configure the pre-push hook](#configure-the-pre-push-hook): Ensure your local changes are validated before pushing to your git server.
- [Add to mapping](#add-to-mapping): You can add an element from your workstation to the synchronized mapping.
- [Add to mapping with dependencies](#add-to-mapping-with-dependencies): You can add an element with associated files from your workstation to the synchronized mapping.
- [Show history](#show-history): You can view the history of the elements up the map in your mapping.
- [Specify processor groups for elements](#specify-processor-groups-for-elements): You can specify a processor group for an element that you can use for the Generate action.
- [Review Mapping Activity](#review-mapping-activity): Review the events that occur in and the status of your mapping.

### Configure the Pre-push Hook

Bridge for Git mappings include a pre-push hook. The pre-push hook validates changes to elements in the repo against changesets in the git server and Endevor. The pre-push hook specifically looks at the fingerprints of the element, the type, the name, and the location in the folder structure. If your changes are out of date (fingerprint does not match) or any of the file or location conventions are not met, then the pre-push hook will prevent you from pushing to the git server.

We recommend that you install the pre-push hook when you start working with a mapping.

When you have a Bridge for Git mapping open in your workspace, Bridge for Git Explorer prompts you to install the pre-push hook. Ensure that you provide your git user name or PAT, depending on your configuration of Bridge for Git.

You can additionally uninstall the pre-push if needed through the command palette.

For more information about how to set up pre-push hooks, see [Set up Hooks](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/using/work-with-git-to-endevor-mappings/set-up-commit-validation-hooks.html).

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

For more information about work-environment Git-Endevor mappings, see [Work with Git to Endevor Mappings](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/endevor-bridge-for-git/3-0/using/work-with-git-to-endevor-mappings.html).

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

Specify a processor group for an element. You can specify a processor group for existing and newly created elements in your mapping.

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

3. Scroll through the operations for the mapping and optionally right-click and select **View Operation Details** for a particular entry.

   If errors occurred, you can see the details with possible solutions.

4. Check the status of the repository.

   If the added element is in the repository already, you can pull the element back to your cloned repository.

You can also set a limit to the number of operations to list in the Mapping Activity section. By default, the number of operations is 100. To change this limit, navigate to VSC **Settings** > **Extensions** > **Bridge for Git Explorer**.

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

Copyright © 2025 Broadcom. The term "Broadcom" refers to Broadcom Inc. and/or its subsidiaries.
