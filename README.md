# ReadMe.md

## Overview

Organizations that want to enable users to receive notifications from the Office 365 Messaging center often find it difficult as they need to add additional Office 365 security roles for non-admin personnel. Now you can sync all Office 365 Messages to a Microsoft Planner plan via a feature available in Office 365.

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner)

Additionally users can create buckets for each service and manually move messages from the receiving bucket into the respective buckets.

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#organize-your-plan-by-service)

Since the service in question exists in the sync'ed message, a user can leverage Power Automate to automatically move those messages into their respective bucket on a nightly basis. In this GitHub repository a user can download the most recent release that contains a solution with a couple of Power Automate Flows built to move messages from the main bucket into their respective service buckets.

Collaborators
Matt Mueller, Microsoft
Valter Herman, Microsoft

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

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/34bd7fb8-aa05-4cbe-aa8c-0de2269a57a0)

### Turn On Planner Syncing

Turn on Planner Syncing from the following instructions:

[Track message center tasks in Planner - Microsoft 365 - Microsoft Planner | Microsoft Learn](https://learn.microsoft.com/en-us/office365/planner/track-message-center-tasks-planner#turn-on-planner-syncing)

## Configuring Power Automate Flows

### Retrieve the _All Messages_ Bucket Id

In order to update the Power Automate flow for sorting, you must retrieve the bucket id for the _All Messages_ bucket. Run the Flow named _List Planner Buckets to get Bucket Id_ with the Group Id and Plan Id for the respective Plan.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/66f5dad6-d365-4cde-8d23-5b3f9297a11c)

Retrieve the id from the successful Flow run.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/bf9bc3fd-eb32-4ef8-9eb5-5eecc71c6fa1)

### Update the Power Automate Flow to Sort Messages

Edit the Flow _Move Tasks to Buckets V2_.

Update the Group Id and Plan Id for the respective Microsoft Planner plan.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/d5adf19a-0517-42d4-bc54-3e754521580c)

Update the Condition step with the bucket id from the previous step.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/966d065e-4eba-4b36-8026-77468a8d91b7)

Update the List Buckets step with respective Microsoft Planner plan.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/55b6908c-7b9f-475c-ae34-97a8e17bb0dc)

Ensure the label colors satisfy your requirement for the respective message category.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/d128894d-9c81-4c5f-8e2e-a5c19e986d20)

Save and run the Flow.

## Example

Below is an example of the end result of this setup.

![image](https://github.com/v7herman4/Planner-Tasks-from-Message-Center/assets/89024016/5ed53e06-7501-4e2e-b2e8-e28c7ae1fc38)

