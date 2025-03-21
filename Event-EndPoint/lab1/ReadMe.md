
# IBM Integration - Creating AsyncAPI

In this lab you will review Kafka Topics that are managed in the Event Endpoint Management inventory.  You will select the FLIGHT.LANDINGS topic and export as AsyncAPI for IBM API Connect Management Portal

[Return to main EEM lab page](../index.md#lab-abstracts)

## About Event Evendpoint Management

As part of your event-driven architecture solution, Event Endpoint Management provides the capability to describe and catalog your Kafka topics as event sources, and to share the details of the topics with application developers within the organization. Application developers can discover the event source and configure their applications to subscribe to the stream of events, providing self-service access to the message content from the event stream.

Access to the event sources are managed by the Event Gateway. The Event Gateway handles the incoming requests from applications to consume from a topic’s stream of events. The Event Gateway is independent of your Kafka clusters, making access control to topics possible without requiring any changes to your Kafka cluster configuration.
## 1.0 Discover EEM Topics

1. Go to **Administration-->Integration Instances**.

    ![](../images/eem0b.png)

1. Click on **my-eem-manager** and open in a new tab.

    **NOTE:** If you already have a tab opened for EEM then go there.

    ![](../images/eem1.png)

1. Now we will login to the eem manager using **eem-admin** user (password provided by instructor).

    **NOTE:** If you receive a certificate exception, in the Firefox browser, click **Advanced** and then click **Accept the Risk and Continue**..

    ![](../images/eem2.png)

1. Once login click on the **Topic icon** on the left side of the page.  This will open the Topics page.

    You should see the **FLIGHT.LANDINGS** topic.

    <span style="color:red">Make sure you clicked on the Topic icon and you are in the Topics page</span>

    Click on the topic name.

    ![](../images/eem3.png)

1. We will now be on the page with all the information for this Topic.   You can view the Schema or Sample Message.

    We will click on the **Export AsyncAPI for IBM API Connect**.

    This will open a window to save the FLIGHT.LANDINGS yaml. Make sure that **Save File** is selected and Click **OK**.

    ![](../images/eem4.png)

## 2.0 Import AsyncAPI into APIC

Now that we have exported the FLIGHT.LANDINGS yaml we will login to the APIC Manager to import it.

1. Now from the Integration Instances select the **apim-demo** and open in a new window.

    ![](../images/apic1.png)

1. Now on the APIC login page make sure you are login already in the upper right corner.   In this example it is "kallus1"

    Click on the login using the **Common Services User Registry**

    ![](../images/apic2.png)

1. Now from the APIC homepage Select the **Develop APIs and products** from the tile or the icon on the left side of the screen.

    ![](../images/apic3.png)

1. Now Click on **Add** and select **API**

      ![](../images/apic4.png)

1. You will see options for OpenAPI and AsyncAPI.   We will select **AsyncAPI**

    But you can also see how you can import OpenAPI's for SOAP, REST, GraphQL.

    ![](../images/apic5.png)

1. Click **Next**

    ![](../images/apic6.png)

1. Now we will select **Drag and drop files here or click to upload**

    ![](../images/apic7.png)

1. This will open the **File Upload window**  You should be in the */student/Downloads* directory.  Select the FLIGHT.LANDINGS.yaml you downloaded from EEM and click Open.  

    ![](../images/apic8.png)

1. It should show that the yaml has been successfully validated.

    Scroll down and click **Next**

    ![](../images/apic9.png)

1. In the *Preview* panel, review API details by scrolling down and click **Next**

    ![](../images/apic10.png)

1. Do not select Activate API. Leave unselected and Click **Next**

    ![](../images/apic11.png)

1. Should now show that the AsyncAPI definition was generated.

    Click **Edit**

    ![](../images/apic12.png)

1. Take a moment to review the elements in the Async API definition. Then go ahead and select the **Develop APIs and products** from the icon on the left side of the screen.

    ![](../images/apic13.png)

1. You will now see your AsyncAPI for FLIGHT.LANDINGS

    ![](../images/apic14.png)

### 2.1 Create new Product for AsyncAPI

Now we will need to create a new Product for AsyncAPI to publish them.  We will be publishing the AsyncAPI to the Event Gateway that is part of Event Automation and is configured in the Event Endpoint Manager.  

1. First we will create a new Product that could be used to include serveral AsyncAPIs. Select the **Add** and select **Product**.

    ![](../images/prd1.png)

1. Choose **New Product** and click **Next**

    ![](../images/prd2.png)

1. Now we will name the Product.  Just call it *AsyncAPIs*.

    Click **Next**

    ![](../images/prd3.png)

1. Here you will see that this product will only be able to be enforced on a gateway type (Event Gateway  Vs API Gateway)

    Select the new FLIGHT.LANDINGS AsyncAPI and click **Next**

    ![](../images/prd4.png)

1. Keep the Default Plan as is and click **Next**

    ![](../images/prd5.png)

1. Click **Next**

    ![](../images/prd6.png)

1. The Summary should show all green.   Click **Done**

    ![](../images/prd7.png)

### 2.2 Publish Product for the Developers to use in the Portal

1. Now go back to the Develop page and select **Products**

    You will see your new AsyncAPIs product.  Click on the three dots on the right and select **Publish**

    ![](../images/prd8.png)

1. On the Publish product screen you will select which catalog you will publish this to. Since we only have the Sandbox catalog select that and click **Next**

    ![](../images/prd9.png)

1. Leave the defaults on this page and Click **Publish**

    ![](../images/prd10.png)

1. You should get a notifiation that this AsyncAPI was published.   You can close it by clicking the "x".

    Click on the **Products** tab then.

    ![](../images/prd11.png)


## RECAP
In this lab you browsed the event catalog provided by IBM Event Endpoint Management and downloaded the AsyncAPI spec for given event description.

Then you imported and published that AsyncAPI in IBM API Connect to expose the corresponding Kafka topic thru the Event Gateway and make it available to potential consumers thru API Connect Dev Portal.

[Return to main EEM lab page](../index.md#lab-abstracts)
