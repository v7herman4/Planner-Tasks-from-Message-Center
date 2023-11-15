# ReadMe.md

## Overview

Organizations that want to enable users to receive notifications from the Office 365 Messaging center often find it difficult as they need to add additional Office 365 security roles for non-admin personnel. Now you can sync all Office 365 Messages to a Microsoft Planner plan via a feature available in Office 365.

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner)

Additionally users can create buckets for each service and manually move messages from the receiving bucket into the respective buckets.

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#organize-your-plan-by-service)

Since the service in question exists in the sync'ed message, a user can leverage Power Automate to automatically move those messages into their respective bucket on a nightly basis. In this GitHub repository a user can download the most recent release that contains a solution with a couple of Power Automate Flows built to move messages from the main bucket into their respective service buckets.

## Security Roles Required

The user installing and configuring the Flow must have at least a Maker role in the Power Platform environment. Additionally the user authenticated for the Connection References must have at least the Office 365 Message Center Reader role.

## License Requirements

For installation and use of the solution, one of the following license types is required:

- Office 365 E3
- Office 365 E5
- Power Automate Premium

## Installing the Solution

### Environment

This solution can be installed in the Default environment. However, it is highly recommended that all solutions that help govern your Office 365 or Power Platform clouds be centralized in one custom environment. If a Center of Excellence Toolkit is installed then that is the ideal environment for such governing automations.

### Import Solution

1. Download the solution from the [latest release.](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/releases)
2. In the Power Platform maker experience, navigate to the target environment and import the solution.

## Configuring Microsoft Planner

### Create a Plan in Microsoft Planner

In order to set up Microsoft Planner to receives messages from the Office 365 Message Center, follow these instructions:

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#how-you-can-use-planner-to-track-your-message-center-tasks)

We recommend naming the bucket _All Messages_.

### Create Separate Service Buckets

In order to create separate buckets for each associated service, follow these instructions:

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#organize-your-plan-by-service)

### Create Labels for Message Categories

For a better visualization of tasks in Microsoft Planner, this automation will leverage labels to identify message categories. Edit the labels in the plan as shown below:

![](RackMultipart20231115-1-eiuegc_html_36c76e3c187cb5a3.png)

### Turn On Planner Syncing

Turn on Planner Syncing from the following instructions:

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#turn-on-planner-syncing)

## Configuring Power Automate Flows

### Retrieve the _All Messages_ Bucket Id

In order to update the Power Automate flow for sorting, you must retrieve the bucket id for the _All Messages_ bucket. Run the Flow named _List Planner Buckets to get Bucket Id_ with the Group Id and Plan Id for the respective Plan.

![](RackMultipart20231115-1-eiuegc_html_9b93b68006873c8d.png)

Retrieve the id from the successful Flow run.

![](RackMultipart20231115-1-eiuegc_html_163ac95f535a6798.png)

### Update the Power Automate Flow to Sort Messages

Edit the Flow _Move Tasks to Buckets V2_.

Update the Group Id and Plan Id for the respective Microsoft Planner plan.

![](RackMultipart20231115-1-eiuegc_html_1f4e09be3860dab8.png)

Update the Condition step with the bucket id from the previous step.

![](RackMultipart20231115-1-eiuegc_html_c3dcfbe425bbaece.png)

Update the List Buckets step with respective Microsoft Planner plan.

![](RackMultipart20231115-1-eiuegc_html_e82c5d3401d432fd.png)

Ensure the label colors satisfy your requirement for the respective message category.

![](RackMultipart20231115-1-eiuegc_html_2bbb881840797d1e.png)

Save and run the Flow.

## Example

Below is an example of the end result of this setup.

![](RackMultipart20231115-1-eiuegc_html_58c02f9030d953e4.png)
