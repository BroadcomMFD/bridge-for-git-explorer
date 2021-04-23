# Bridge for Git Explorer

The Bridge for Git Explorer allows you to work with Git-Endevor mappings
synchronized to CA Endevor using the CA Endevor Bridge for Git. When you work
with a work environment only mapping, you may need to add elements from up the
Endevor map back to your mapping. The Bridge for Git Explorer reads the
information about the mapping that you have cloned locally in your VS Code
workspace and provides a list of elements from up the map for
that particular CA Endevor inventory location.

## Prerequisites

- Visual Studio Code v1.50.0 or higher
- CA Endevor version 18.1 with the following PTFs:
   - PTF S012309 for versioning of the REST API  
   **Note:** Bridge for Git Explorer only works with v2 of the REST API
- CA Endevor Bridge for Git
- CA Endevor Plug-in for Zowe CLI version 6.1.0 or higher
- CA Endevor Bridge for Git for Zowe CLI version 2.0.1 or higher
- A CA Endevor Plug-in for Zowe CLI profile or an API ML base profile.  
  This profile should have the same configuration of CA Endevor used for
  the Git-Endevor mapping you have open in your workspace.
- A CA Endevor Bridge for Git Plug-in for Zowe CLI profile with Git credentials.  
  This profile should contain the information for the same Bridge for
  Git server you used to create the mapping.
- A synchronized Git-Endevor mapping that you have cloned locally and have
  open in your VS Code workspace.

## Profiles

If you have a CA Endevor SCM Plug-in for Zowe CLI profile or API ML base profile
configured, the extension will use the credentials for that profile to provide you
with the list of elements that you can add to your synchronized mapping. For more information about creating an Endevor profile in Zowe CLI, see
[CA Endevor SCM Plug-in for Zowe CLI](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-brightside/3-0/ca-brightside-command-line-interface-cli/available-cli-plug-ins/ca-brightside-plug-in-for-ca-endevor-scm.html).

To add an element to your mapping, ensure that you have a CA Endevor Bridge for Git for Zowe CLI plug-in profile. For more information about creating this profile, see [CA Endevor Bridge for Git Plug-in for Zowe CLI](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-brightside/3-0/ca-brightside-command-line-interface-cli/available-cli-plug-ins/CA-Endevor-Bridge-for-Git-Plug-in-for-Zowe-CLI.html).

**Note:** If you do not have a profile created for the instance of Endevor web services that was used to create the synchronized Git-Endevor mapping, the application will prompt you to supply your mainframe credentials for that web services instance. The application then creates a session during which you can add elements to your mapping.

## Getting Started

You have your work environment mapping in your workspace and are ready to use
the extension.

**Follow these steps:**

1. Select the Bridge for Git Explorer icon from the left panel with your installed
   extensions.  
   The extension opens and the name and branch of your work environment mapping appear
   in the tree.
2. Click on the name of the mapping to expand the tree.
3. View the available systems, subsystems, and elements for the CA Endevor
   inventory location by clicking through the folders in the tree.

Click on an element to view its contents. To see the location details of an element, you can hover your mouse over the element or right + click and select "View details."

## Add an element to your mapping

After you navigate the Endevor map and find the needed element, you can select and add
it to your synchronized mapping. Once it is added to the synchronized mapping, you can
bring it into your local branch. There are two choices for adding an element, "Add to mapping"
and "Add to mapping with dependencies".

### Add to mapping

**Follow these steps:**

1. Right + click the element you want to add and select
   "Add to mapping".  
   You receive a message that your request has been
   queued.
2. Run a `git pull` command in the command line to bring the element into your local
   copy of the repository.  
   Your element is now available to work with in your local copy of the repository.

**Note:** The retrieval of the element can take some time. Rather than running `git pull`
immediately, you can navigate to your enterprise Git server to check for the added element
from the automatic Endevor synchronization.

### Add to mapping with dependencies

In the above procedure, you can also select "Add to mapping with dependencies". This brings the
associated files with the element you have selected.  
**Note:** Developers are limited to only 50 dependencies for a particular element.

## More information

For more information about work environment Git-Endevor mappings, see [Work with Synchronized Repositories](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/use-the-ca-enterprise-git-bridge/work-with-git-endevor-mappings.html).  

For a general overview of Bridge for Git, see [CA Endevor Bridge for Git](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git.html).

## Troubleshooting

The following section details how to troubleshoot Bridge for Git Explorer and common issues.

### View output information

For most issues in Bridge for Git Explorer, you can view specific information related to an error message in the output stream of the extension.

**Follow these steps:**

1. Open a new terminal.
2. Select the "OUTPUT" tab.
3. Select "Bridge for Git Explorer" in the dropdown at right.

## F.A.Q.

**Q:** You receive the message _"Failed to create <profile> Profile Manager. See Bridge for Git output stream for more info."_  
**A:** View the output stream information. Ensure that your profiles information is accurate and your password and token are still valid.

**Q:** You receive the message _"No valid Endevor Bridge for Git profile found for hostname host:port."_  
**A:** Ensure that you have an Endevor Bridge for Git profile that uses the same host and port information of CA Endevor web services that was used for your synchronized Git-Endevor mapping.
