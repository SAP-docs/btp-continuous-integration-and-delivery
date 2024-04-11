<!-- loio74fe5409efad4efaae017eb90fa64b95 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Additional Variables

Add environment variables that store user-defined strings to the stages of your SAP Continuous Integration and Delivery jobs.

> ### Note:  
> You can use this feature for all scenarios listed in [Configuring Jobs](configuring-jobs-e293286.md) except for  <?sap-ot O2O class="- topic/xref " href="019ed685a19b4efab4f7df0e108d1697.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/74fe5409efad4efaae017eb90fa64b95.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

You can configure environment variables either using the SAP Continuous Integration and Delivery job editor or using the configuration file in your source code management system.

<a name="task_svr_lnl_jwb"/>

<!-- task\_svr\_lnl\_jwb -->

## Add Additional Variables Using the Job Editor

Add environment variables to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_svr_lnl_jwb__steps_ay4_l4w_dwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add credentials variables and choose *Edit*.

2.  In the *Stages* tab of your job, navigate to the stage to which you want to add environment variables and choose :heavy_plus_sign: next to *Additional Variables*.

3.  In the *Name* text field, enter a name for your variable. Use only letters, digits, and underscores.

4.  In the *Value* field, enter a string value for your variable.

5.  Choose *Create*.

    Now every script that is executed within the stage has access to the environment variable you just created.




<a name="task_svr_lnl_jwb__postreq_kws_gnt_jwb"/>

## Next Steps

Once you've set up your environment variables, you can use them in your scripts within a specific stage as follows:

```
!#/bin/bash
echo "Injected variable: $MyVar"
```

Replace `MyVar` with the name of the variable you've just created.

<a name="task_j3h_t3w_dwb"/>

<!-- task\_j3h\_t3w\_dwb -->

## Add Additional Variables in the Configuration File

Add environment variables to your job using the configuration file in your source code management system.



<a name="task_j3h_t3w_dwb__steps_yxn_j4w_dwb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the service section, depending on the stage in which you want to set the variable \(in this example, we used the "Build" stage\), insert the following code block. Assign your own values to the `name` and `value` parameters:

    ```
    service:
      stages:
        Build:
          stringVariables:
            - name: "MyVar"
              value: "blogs.sap.com"
    ```

    > ### Note:  
    > For `name`, use only letters, digits, and underscores.

    Now every script that is executed in the stage has access to the environment variable you just created.




<a name="task_j3h_t3w_dwb__postreq_uxg_qnt_jwb"/>

## Next Steps

Once you've set up your environment variables, you can use them in your scripts within a specific stage as follows:

```
!#/bin/bash
echo "Injected variable: $MyVar"
```

Replace `MyVar` with the name of the variable you've just created.

