# B4G-vscode-extension

The Bridge for Git Explorer allows you to work with Git-Endevor mappings
synchronized to CA Endevor via the CA Endevor Bridge for Git. When you work
with a work environment only mapping, you may need to add elements from up the
Endevor map back to your mapping. The Bridge for Git Explorer reads the
information about the mapping that you have cloned locally in your VS Code
workspace and provides a list of elements from up the map (first-found) for
that particular CA Endevor inventory location.

## Prerequisites

- A CA Endevor Plug-in for Zowe CLI profile or an API ML base profile
  This profile should have the same configuration of CA Endevor used for
  the Git-Endevor mapping you have open in your workspace.
- A CA Endevor Bridge for Git Plug-in for Zowe CLI profile with Git credentials
  This profile should contain the information for the same Bridge for
  Git server you used to create the mapping.
- A synchronized Git-Endevor mapping that you have cloned locally and have
  opened in your VS Code workspace

## Profiles

If you have a CA Endevor Plug-in for Zowe CLI profile or API ML base profile
configured, the extension will use the credentials for that profile to run the
REST API call to the mainframe in order to provide you with the list of
elements that you can add to your synchronized mapping.

## Getting Started

When you are working with your work environment mapping in your workspace and
need an element from up the map, select the Bridge for Git Explorer icon from
the left panel with your installed extensions. The extension opens and the name
and branch of your work environment mapping appear in the tree. Click the name
of the mapping to expand the tree and view the available systems,
subsystems, and elements for the CA Endevor inventory location.

## Adding back an element

Navigate to the particular element you need by clicking through the system(s)
and subsystem(s) for your CA Endevor inventory location. Once you have expanded
the tree and found the the element you need, right + click and select
"Add to mapping". You receive a message that your request has been
queued. You can also select "Add to mapping with dependencies". This brings the
associated files with the element you have selected. Note: Developers are
limited to only 50 dependencies for a particular element.

Go to the enterprise Git repository of your Git-Endevor mapping. Bridge for Git
brings the element into the synchronized mapping. You will find your added element
in the enterprise Git server. In your IDE, open a terminal and complete a "git pull"
command. This brings the element to your local working directory.

## Limits on adding elements

## More information

For more information about work environment Git-Endevor mappings, see [Work with Synchronized Repositories](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git/use-the-ca-enterprise-git-bridge/work-with-git-endevor-mappings.html)
For a general overview of Bridge for Git, see [CA Endevor Bridge for Git](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-endevor-integrations-for-enterprise-devops/1-0/ca-endevor-bridge-for-git.html)
