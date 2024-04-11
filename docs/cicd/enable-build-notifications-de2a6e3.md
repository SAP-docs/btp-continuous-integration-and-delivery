<!-- loiode2a6e36982e48bbacfcd038567a5e8e -->

# Enable Build Notifications

Enable automatic triggering of notifications about build events using the SAP Alert Notification service for SAP BTP.



<a name="loiode2a6e36982e48bbacfcd038567a5e8e__prereq_stg_5hw_pqb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have an existing job in SAP Continuous Integration and Delivery. See [Configuring a Job](enhancing-jobs-d581ab5.md).

-   You habe enabled the SAP Alert Notification service and created a service key to authenticate your pipeline against SAP Alert Notification service. See [Initial Setup](https://help.sap.com/docs/ALERT_NOTIFICATION?version=Cloud) and [Credential Management](https://help.sap.com/docs/ALERT_NOTIFICATION/5967a369d4b74f7a9c2b91f5df8e6ab6/80fe24f86bde4e3aac2903ac05511835.html?version=Cloud).




## Context

When you enable build notifications in SAP Continuous Integration and Delivery, the pipeline will automatically send notifications about build events to SAP Alert Notification service. Use the Alert Notification service to manage the build notifications and consume them using the system of your choice, such as email, Slack, and other channels. For more information, see [SAP Alert Notification service for SAP BTP](https://help.sap.com/docs/ALERT_NOTIFICATION?version=Cloud).



## Procedure

1.  In SAP Continuous Integration and Delivery, navigate to your job and choose *Edit*.

2.  In the detail view of your job, navigate to the *Build Notification* tab and perform the following actions:

    **Configuring build notifications in SAP Continuous Integration and Delivery**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    Either switch the execution of *Send Build Notifications via SAP Alert Notification Service* on or off.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Service Key
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against SAP Alert Notification service, create a *Service Key* credential. See [Creating Credentials](creating-credentials-6658c81.md).

    In the **Service Key** text field, enter the already created service key of your Alert Notification service instance.

    Choose this service key credential from the dropdown list.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Custom Tag
    
    </td>
    <td valign="top">
    
    \(Optional\) Add a tag to the notification.
    
    </td>
    </tr>
    </table>
    
3.  Choose *Save*.




<a name="loiode2a6e36982e48bbacfcd038567a5e8e__result_xgs_wjn_15b"/>

## Results

You've enabled automatic triggering of build notifications. Your SAP Alert Notification service instance will now receive events from your build.



<a name="loiode2a6e36982e48bbacfcd038567a5e8e__postreq_xww_vjn_15b"/>

## Next Steps

You can customize your build notifications and create subscriptions using the SAP Alert Notification service. For more information, see [Configuration Management Using the SAP BTP Cockpit](https://help.sap.com/docs/ALERT_NOTIFICATION/5967a369d4b74f7a9c2b91f5df8e6ab6/033cbf7cfab2484abad90276d3d3e776.html?version=Cloud). Use the following table as a guide for the integration between the services.



### Event Property Mapping

Based on where an event happens in your SAP Continuous Integration and Delivery pipeline \(during the build or in a specific stage or step\), the event properties can be mapped to SAP Alert Notification service event properties as follows:

**Event property mapping between SAP Alert Notification service and SAP Continuous Integration and Delivery**


<table>
<tr>
<th valign="top" rowspan="2">

SAP Alert Notification Service Event Property

</th>
<th valign="top" colspan="3">

SAP Continuous Integration and Delivery Event Property

</th>
<th valign="top" rowspan="2">

Description

</th>
</tr>
<tr>
<th valign="top">

Build Value

</th>
<th valign="top">

Stage Value

</th>
<th valign="top">

Step Value

</th>
</tr>
<tr>
<td valign="top">

`eventType` 

</td>
<td valign="top">

-   `build.start`

-   `build.end`




</td>
<td valign="top">

-   `build.stage.start`

-   `build.stage.end`




</td>
<td valign="top">

`build.log` 

</td>
<td valign="top">

The event type used to distinguish the event.

> ### Note:  
> If a build has finished with status *Aborted*, no `build.end` or `build.stage.end` events are sent to Alert Notification service.



</td>
</tr>
<tr>
<td valign="top">

`severity` 

</td>
<td valign="top" colspan="2">

-   `INFO` - build or stage has started and finished successfully

-   `WARNING` - build is unstable

-   `ERROR` - build or stage has failed




</td>
<td valign="top">

-   `WARNING` - log level is `warning`

-   `ERROR`- log level is `error`

-   `FATAL`- log level is `fatal`




</td>
<td valign="top">

The event severity.

</td>
</tr>
<tr>
<td valign="top">

`category` 

</td>
<td valign="top" colspan="2">

-   `NOTIFICATION` - build or stage is successful

-   `EXCEPTION` - build or stage has failed




</td>
<td valign="top">

-   `ALERT` - log level is `warning` 

-   `EXCEPTION` - log level is `error`, `fatal`, or `panic`




</td>
<td valign="top">

The event category.

</td>
</tr>
<tr>
<td valign="top">

`subject` 

</td>
<td valign="top">

-   `Build has started` 

-   `Build has finished with <status>` 

-   `Build has finished with <status> in stage <stage>`




</td>
<td valign="top">

-   `Stage <stage> has started`

-   `Stage <stage> has finished with <status>`




</td>
<td valign="top">

`Build step <step> sends <severity>` 

</td>
<td valign="top">

A short description of the build status.

For more information about the build statuses, see [Running and Monitoring CI/CD Jobs](running-and-monitoring-ci-cd-jobs-db8521c.md).

</td>
</tr>
<tr>
<td valign="top">

`body` 

</td>
<td valign="top">

-   `Build has started` 

-   `Build has finished with <status>` 

-   `Build has finished with <status> in stage <stage>`




</td>
<td valign="top">

-   `Stage <stage> has started`

-   `Stage <stage> has finished with <status>`




</td>
<td valign="top">

`<step log message>` 

</td>
<td valign="top">

A long description of the pipeline status.

</td>
</tr>
<tr>
<td valign="top">

`tags.ans:correlationId` 

</td>
<td valign="top" colspan="3">

`<build id>` 

</td>
<td valign="top">

The unique ID of the build.

</td>
</tr>
<tr>
<td valign="top">

`tags.ans:sourceEventId` 

</td>
<td valign="top" colspan="3">

`<build id>` 

</td>
<td valign="top">

The unique ID of the build.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:stage` 

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`<build stage>`

</td>
<td valign="top">

n/a

</td>
<td valign="top">

The stage that triggered the event.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:stepName` 

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`<build step>`

</td>
<td valign="top">

The name of the step that triggered the event.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:issuer` 

</td>
<td valign="top" colspan="3">

`SAP Continuous Integration and Delivery` 

</td>
<td valign="top">

The service name.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:errorCategory` 

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
<td valign="top">

`<step error category>` 

</td>
<td valign="top">

\(In case of error\) The error category from the build step.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:logLevel` 

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
<td valign="top">

-   `warning`

-   `error`

-   `fatal`

-   `panic`




</td>
<td valign="top">

The log level from the build step.

</td>
</tr>
<tr>
<td valign="top">

`tags.cicd:custom` 

</td>
<td valign="top" colspan="3">

`<custom tag>` 

</td>
<td valign="top">

\(Optional\) Custom tag defined in the user interface.

</td>
</tr>
<tr>
<td valign="top">

`resource.resourceName` 

</td>
<td valign="top" colspan="3">

`<job name>` 

</td>
<td valign="top">

The unique name of the pipeline job.

</td>
</tr>
<tr>
<td valign="top">

`resource.resourceType` 

</td>
<td valign="top" colspan="3">

`<pipeline name>` 

</td>
<td valign="top">

The pipeline name.

For a full list of the supported pipelines, see [Configuring Jobs](configuring-jobs-e293286.md).

</td>
</tr>
<tr>
<td valign="top">

`resource.resourceInstance` 

</td>
<td valign="top" colspan="3">

`<build id>` 

</td>
<td valign="top">

The unique ID of the build.

</td>
</tr>
<tr>
<td valign="top">

`resource.tags.cicd:repository` 

</td>
<td valign="top" colspan="3">

`<repository url>` 

</td>
<td valign="top">

\(If applicable\) The URL to your source code management system repository.

</td>
</tr>
<tr>
<td valign="top">

`resource.tags.cicd:commitish` 

</td>
<td valign="top" colspan="3">

`<commit id>` 

</td>
<td valign="top">

\(If applicable\) The name of the branch or commit ID.

</td>
</tr>
<tr>
<td valign="top">

`resource.tags.cicd:buildURL` 

</td>
<td valign="top" colspan="3">

`<build url>` 

</td>
<td valign="top">

The URL to the build.

</td>
</tr>
</table>

