<!-- loio72a6ec570ecf43569ee9b85539335138 -->

# Azure IoT Hub

Consume Azure IoT Hub with SAP Private Link service.



<a name="loio72a6ec570ecf43569ee9b85539335138__section_ls4_n2w_1bc"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

**resourceId** \(required\)

</td>
<td valign="top">

Identifies the resource on Azure the private link should be created for.

</td>
</tr>
<tr>
<td valign="top">

**subResource** \(required\)

</td>
<td valign="top">

Identifies the subresource on Azure the private link should be created for. Must be `iotHub`.

</td>
</tr>
<tr>
<td valign="top">

**requestMessage** \(optional\)

</td>
<td valign="top">

Specifies a message which is shown for the approval request on Azure for the specified resource.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Devices/IotHubs/my-iot-hub",
>     "subResource": "iotHub",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio72a6ec570ecf43569ee9b85539335138__section_brd_1fw_1bc"/>

## Binding Credentials

The following binding credentials are provided:


<table>
<tr>
<td valign="top">

**hostname**

</td>
<td valign="top">

This DNS entry resolves to the internal IP address associated with this private link.

</td>
</tr>
<tr>
<td valign="top">

**eventHubCompatibleEndpointHostname**

</td>
<td valign="top">

DNS entry for connecting to the internal IP address associated with the built-in Event Hubs compatible endpoint.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "my-iot-hub.azure-devices.net",
>                 "eventHubCompatibleEndpointHostname": "iothub-ns-john-xxx.servicebus.windows.net"
>             }
>         }
>     ]
> }
> ```



<a name="loio72a6ec570ecf43569ee9b85539335138__section_pfdb_dfm_3fw_1bc"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure IoT Hub via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

