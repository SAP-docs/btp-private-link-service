<!-- loioa204b7930c4f4dd0a7cae3dcabf32735 -->

# Azure Cache for Redis

Consume Azure Cache for Redis and Redis Enterprise with SAP Private Link service.



<a name="loioa204b7930c4f4dd0a7cae3dcabf32735__section_exp_t2b_pxb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:

****


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

Identifies the subresource on Azure the private link should be created for.



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
> Azure Cache for Redis
> 
> ```
> {
>      "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Cache/Redis/myredis",
>      "subResource": "redisCache",
>      "requestMessage": "Please approve connection"
>  }
> ```

> ### Sample Code:  
> Azure Cache for Redis Enterprise
> 
> ```
> {
>      "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Cache/RedisEnterprise/myredisenterprise",
>      "subResource": "redisEnterprise",
>      "requestMessage": "Please approve connection"
>  }
> ```



<a name="loioa204b7930c4f4dd0a7cae3dcabf32735__section_xq4_sfb_pxb"/>

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

**hostname**



</td>
<td valign="top">

DNS entry to connect to the Azure resource. This DNS entry resolves to the internal IP address associated with this private link.



</td>
</tr>
</table>

> ### Sample Code:  
> Azure Cache for Redis
> 
> ```
> {
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "myredis.redis.cache.windows.net"
>              }
>          }
>      ]
>  }
> ```

> ### Sample Code:  
> Azure Cache for Redis Enterprise
> 
> ```
> {
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "myredisenterprise.westeurope.redisenterprise.cache.azure.net"
>              }
>          }
>      ]
>  }
> ```



<a name="loioa204b7930c4f4dd0a7cae3dcabf32735__section_gnt_yfb_pxb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure Cache for Redis or RedisEnterprise via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

