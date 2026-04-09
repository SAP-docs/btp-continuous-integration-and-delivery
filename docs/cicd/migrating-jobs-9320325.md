<!-- loio93203258b7b24ba7936a986b71271a77 -->

# Migrating Jobs

Learn how to migrate existing Cloud Foundry Environment jobs from version 2.0 to version 3.0.



<a name="loio93203258b7b24ba7936a986b71271a77__section_qws_tzx_dgc"/>

## Context

The Cloud Foundry Environment pipeline has been updated to version 3.0 to enhance functionality and user experience. This update brings several important improvements:

-   The configuration file structure has been streamlined, making it more compact, user-friendly, and easier to manage.

-   The config file format in the repository now matches the API format, ensuring consistency and reducing complexity.

-   Technical enhancements have been made to improve performance and reliability.

-   The user interface has been simplified for a more intuitive and efficient user experience.

-   New features have been added: You can now specify your project's build descriptor, which refers to the location of your `mta.yaml`, `package.json`, or `pom.xml` file. Additionally, MTA extension descriptors are now supported. For more information, see [Configure a Cloud Foundry Environment Job](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3).


Depending on the configuration mode of your existing Cloud Foundry Environment jobs in version 2.0, you may need to take specific actions to ensure a smooth transition to pipeline version 3.0.



<a name="loio93203258b7b24ba7936a986b71271a77__section_itq_vxs_ngc"/>

## Jobs Configured in the Job Editor

Cloud Foundry Environment jobs configured in the job editor do not require any manual configuration changes for their migration to pipeline version 3.0. To migrate a job, use the *Migrate* button in the detail view of the respective job. If you need assistance with migrating a larger number of jobs, please open a support ticket as described in [Support, Feature Requests, and Feedback](support-feature-requests-and-feedback-6e10ad4.md).

> ### Note:  
> If you do not migrate your jobs by February 3, 2026, they will be automatically migrated.



<a name="loio93203258b7b24ba7936a986b71271a77__section_icb_zxs_ngc"/>

## Jobs Configured in the Source Repository

Version 3.0 of the Cloud Foundry Environment pipeline requires updates to the repository configuration of jobs configured in the source repository to ensure they continue to function properly after migration. We offer a converter tool that provides you with an updated version of your original configuration. This converter tool covers standard use cases and is part of the migration workflow in the user interface. If your configuration contains custom settings that cannot be converted using the converter, please open a support ticket as described in [Support, Feature Requests, and Feedback](support-feature-requests-and-feedback-6e10ad4.md).



### Procedure

> ### Note:  
> Before migrating a job to pipeline version 3.0, consider creating a backup by choosing *Copy* in its detail view. Please note that the migration cannot be undone.

1.  In the *Jobs* tab in SAP Continuous Integration and Delivery, choose your job from the table.

    This opens the detail view of your job.

2.  In the toolbar at the top of your job's detail view, choose *Migrate*.

    This opens the *Migrate to Pipeline Version 3.0* pop-up.

3.  In the *Original Job Configuration* text area, paste the content of the `.pipeline/config.yml` file from your repository.

    Your original configuration remains unchanged in the `.pipeline/config.yml` file. The updated configuration needs to be saved in a new file in your repository.

4.  Choose *Next*.

5.  Copy the provided updated job configuration into a file named `.sap_cid/config.yml` in your repository. Commit your changes to your source code management system, ensuring that the new file and its content are included.

6.  Choose *Migrate* to finalize the migration.


> ### Caution:  
> If you do not migrate your jobs by February 3, 2026, they will be automatically migrated. Jobs configured in the source repository whose configuration has not been updated will not function anymore after their migration.

