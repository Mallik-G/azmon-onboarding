# Azure Monitor Onboarding Guide

This guide is intended to help Azure customers attempting to setup monitoring on a large Azure environment get set up and maintain that state over time.

## Introduction
As the breadth of Azure’s service offerings increases and the size of your Azure environment grows, the pain of onboarding that environment to a new monitoring tool increases too. Particularly when onboarding a large number of Azure resources to [Log Analytics](http://aka.ms/ladocs) or a [3rd party SIEM tool](http://aka.ms/azmoneventhub), it can be cumbersome to have to set up monitoring resource-by-resource, and an ongoing challenge to keep things set up as resources are created and deleted. To help alleviate some of that pain, we’ve put together this guide to help you with these two situations:
* You want to rapidly connect a large Azure environment to Log Analytics and want all resources (including Virtual Machines) to send log and metric data to your Log Analytics workspace. Once you’ve done that, you want to make sure that any new resources are automatically set up to do this for you.
* You want to rapidly connect a large Azure environment to a 3rd party SIEM tool and you want all resources to send log data to [an Event Hubs namespace, where it can be consumed by a SIEM connector](http://aka.ms/azmoneventhub). Once you’ve done that, you want to make sure that any new resources are automatically set up to do this for you.

For either situation, the basic steps are the same:

1. Enable an Azure Policy initiative or individual policies to ensure that any new resource is automatically setup when it is created (often called “greenfield” enablement).
2. Run a script to set things up on existing resources (often called “brownfield” enablement).

...and that’s it! The rest of this guide walks through this process in detail.

## Send data to Log Analytics
This guide shows you how to set up Log Analytics to monitor two types of Azure data:

* **Virtual Machines** - For Azure Resource Manager virtual machines, you install the OMS agent on either [Linux](https://docs.microsoft.com/azure/virtual-machines/extensions/oms-linux) or [Windows](https://docs.microsoft.com/azure/virtual-machines/extensions/oms-windows) using the Azure VM extensions and include the OMS workspace ID and key in the VM extension settings.
* **Azure Resource Diagnostic Logs** - For [Azure Resource Diagnostic Logs](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs), you create a Resource Diagnostic Setting on the resource you want to send the data, and [specify the OMS workspace where you want the data to go](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitor-stream-diagnostic-logs-log-analytics).

You can also [set up your Azure Activity Log to go to Log Analytics manually](https://docs.microsoft.com/azure/log-analytics/log-analytics-activity#configuration).

### Step 1: Setup policy for greenfield enablement

### Step 2: Run scripts for brownfield enablement

## Send data to Event Hubs
This guide shows you how to set up Azure Monitor to send data to SIEMs for two types of Azure data:

* **Azure Resource Diagnostic Logs** - For [Azure Resource Diagnostic Logs](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs), you create a Resource Diagnostic Setting on the resource you want to send the data, and [specify the Event Hubs namespace where you want the data to end up](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-stream-diagnostic-logs-to-event-hubs).
* **Azure Activity Log** - For [the Azure Activity Log](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs), you create a Subscription Diagnostic Setting on the subscription from which you want the Activity Log data to be sent, and [specify the Event Hubs namespace where you want the data to end up](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs).

You can also send other types of Azure Monitor data to Event Hubs by [setting them up manually](http://aka.ms/azmoneventhub).

### Step 1: Setup policy for greenfield enablement

### Step 2: Run scripts for brownfield enablement
