<!-- loio72a36460d799477a889b8802b6734462 -->

# Configure DNS on Kyma



<a name="loio72a36460d799477a889b8802b6734462__section_rpy_5s2_vzb"/>

## Prerequisites

-   You have set up SAP Private Link Service

-   You have connected SAP Private Link Service to Microsoft Azure Private Link Service



<a name="loio72a36460d799477a889b8802b6734462__section_psr_xs2_vzb"/>

## Overview

The last step of connecting SAP Private Link Service is the binding of the application to a service instance. As a result of the creation of a binding between you application and a private link service instance, a secret that contains the binding credentials is created. That secret contains information about the private link endpoint in the form of FQDN and internal \(private\) IP address. There are various options in configuring the kyma cluster DNS so that the internal IP address is resolved from the FQDN.



<a name="loio72a36460d799477a889b8802b6734462__section_qqx_ys2_vzb"/>

## Option 1: Add entries to `/etc/hosts` file of the Pod using `.spec.hostAliases`

This is a pod-wise solution. Lets say FQDN is `someresource.privatelink.blob.core.windows.net` and the internal IP is `10.250.1.5`. The pod can be configured to resolve both the public FQDN of the resource `someresource.blob.core.windows.net` and the privatelink FQDN of the resource `someresource.privatelink.blob.core.windows.net` to the private IP `10.250.1.5`. This can be done by adding `hostAliases` to the yaml of the pod as shown in the following example:

> ### Sample Code:  
> ```
> apiVersion: v1
> kind: Pod
> metadata:
>   name: hostaliases-pod
> spec:
>   hostAliases:
>   - ip: "10.250.1.5"
>     hostnames:
>     - "someresource.blob.core.windows.net"
>     - "someresource.privatelink.blob.core.windows.net"
>   restartPolicy: Always
>   containers:
>   - name: hostaliases-pod
>   image: ....
>   ...
> ```



<a name="loio72a36460d799477a889b8802b6734462__section_exk_4t2_vzb"/>

## Option 2: Add DNS entries via custom configuration of `CoreDNS`

This is a cluster-wise solution that is explained in [Custom DNS Configuration](https://gardener.cloud/docs/gardener/custom-dns-config/).

Using as example FQDN `someresource.privatelink.blob.core.windows.net` and internal IP `10.250.1.5`, the following `ConfigMap` will change the configuration of `CoreDNS` so that `someresource.blob.core.windows.net` and `someresource.privatelink.blob.core.windows.net` will be resolved to the internal IP `10.250.1.5`:

> ### Sample Code:  
> ```
> apiVersion: v1
> data:
>   pls-custom.server: |
>     blob.core.windows.net:8053 {
>           errors
>           log
>           template IN ANY someresource.blob.core.windows.net {
>               answer "someresource.blob.core.windows.net 60 IN CNAME someresource.privatelink.blob.core.windows.net"
>           }
>           hosts {
>             10.250.1.5 someresource.privatelink.blob.core.windows.net
>             fallthrough
>           }
>       }
> kind: ConfigMap
> metadata:
>   annotations:
>     resources.gardener.cloud/ignore: "true"
>   name: coredns-custom
>   namespace: kube-system
> ```



<a name="loio72a36460d799477a889b8802b6734462__section_wz3_c52_vzb"/>

## Limitations

Custom DNS configuration will not work as expected if [NodeLocalDNS](https://gardener.cloud/docs/gardener/node-local-dns/) is enabled. On a standard kyma cluster `NodeLocalDNS` is enabled by default.

The least disruptive workaround when NodeLocalDNS is enabled is to disable forwarding of requests to upstream DNS, which can be done via option `disableForwardToUpstreamDNS` in the Shoot resource.



<a name="loio72a36460d799477a889b8802b6734462__section_xrp_y52_vzb"/>

## Option 3: Istio DNS Proxying

[DNS Proxying](https://istio.io/latest/docs/ops/configuration/traffic-management/dns-proxy/) is a feature of istio that can be used to add custom DNS entries. This usually is done in three steps:

1.  Enable istio DNS Proxying if it's not enabled

    -   this feature can be enabled during istio installation with the command:

        > ### Sample Code:  
        > ```
        > cat <<EOF | istioctl install -y -f -
        > apiVersion: install.istio.io/v1alpha1
        > kind: IstioOperator
        > spec:
        >   meshConfig:
        >     defaultConfig:
        >       proxyMetadata:
        >         # Enable basic DNS proxying
        >         ISTIO_META_DNS_CAPTURE: "true"
        >         # Enable automatic address allocation, optional
        >         ISTIO_META_DNS_AUTO_ALLOCATE: "true"
        > EOF
        > ```


    -   or on a specific pod by adding `proxy.istio.io/config` annotation:

        > ### Sample Code:  
        > ```
        > kind: Deployment
        > metadata:
        > name: sleep
        > spec:
        > ...
        >   template:
        >     metadata:
        >       annotations:
        >         proxy.istio.io/config: |
        >           proxyMetadata:
        >             ISTIO_META_DNS_CAPTURE: "true"
        >             ISTIO_META_DNS_AUTO_ALLOCATE: "true"
        > ...
        > ```


2.  Enable injection of istio sidecar proxy

    -   either enable injection at the namespace level by using

        > ### Sample Code:  
        > ```
        > $ kubectl label namespace <replace-with-your-namespace> istio-injection=enabled --overwrite
        > ```


    -   or enable on a specific pod by configuring the `sidecar.istio.io/inject` label on the pod

        > ### Note:  
        > Injection occurs at pod creation time. The pod mast be deleted to make sure it is created with the injected sidecar.


3.  1.  Add `ServiceEntry`'s with `hosts` and `addresses` spec


    The following example `ServiceEntry` makes sure that `someresource.blob.core.windows.net` and `someresource.privatelink.blob.core.windows.net` are resolved to the internal IP `10.250.1.5`:

    > ### Sample Code:  
    > ```
    > apiVersion: networking.istio.io/v1beta1
    > kind: ServiceEntry
    > metadata:
    >   name: external-address-privatelink
    > spec:
    >   addresses:
    >   - 10.250.1.5
    >   hosts:
    >   - plsintegrtestv2ragrs.privatelink.blob.core.windows.net
    >   - plsintegrtestv2ragrs.blob.core.windows.net
    >   ports:
    >   - name: https
    >     number: 443
    >     protocol: https
    > ```


