---

copyright:
  years: 2017, 2020

lastupdated: "2020-02-10"

keywords: endpoint, location, object storage

subcollection: cloud-object-storage

---
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:table: .aria-labeledby="caption"}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
{:help: data-hd-content-type='help'}

# Endpoints and storage locations
{: #endpoints}

Sending a REST API request or configuring a storage client requires setting a target endpoint or URL. Each storage location has its own set of URLs.
{: shortdesc}

Private endpoints can be used from within the {{site.data.keyword.cloud_notm}} and don't incur data transfer charges. Public endpoints can be used from outside the {{site.data.keyword.cloud_notm}} and do incur transfer charges. If possible, it's best to use a private endpoint.

Direct endpoints are used by workloads running in an {{site.data.keyword.cloud_notm}} [Virtual Private Cloud](/docs/vpc?topic=vpc-about-vpc).

All {{site.data.keyword.cos_full}} endpoints support TLS 1.2 encryption.
{: note}

## Regional Endpoints
{: #endpoints-region}

Buckets that are created at a regional endpoint distribute data across three data centers that are spread across a metro area. Any one of these data centers can suffer an outage or even destruction without impacting availability.

| Region            | Type   | Endpoint                                           |
|-------------------|--------|----------------------------------------------------|
| US South          | Public | `s3.us-south.cloud-object-storage.appdomain.cloud` |
| US East           | Public | `s3.us-east.cloud-object-storage.appdomain.cloud`  |
| EU United Kingdom | Public | `s3.eu-gb.cloud-object-storage.appdomain.cloud`    |
| EU Germany        | Public | `s3.eu-de.cloud-object-storage.appdomain.cloud`    |
| AP Australia      | Public | `s3.au-syd.cloud-object-storage.appdomain.cloud`   |
| AP Japan          | Public | `s3.jp-tok.cloud-object-storage.appdomain.cloud`   |
{: class="simple-tab-table"}
{: caption="Table 1. Regional Endpoints" caption-side="top"}
{: #regionalendpointtable1}
{: tab-title="Public"}
{: tab-group="Regional-endpoints"}

| Region            | Type    | Endpoint                                                   |
|-------------------|---------|------------------------------------------------------------|
| US South          | Private | `s3.private.us-south.cloud-object-storage.appdomain.cloud` |
| US East           | Private | `s3.private.us-east.cloud-object-storage.appdomain.cloud`  |
| EU United Kingdom | Private | `s3.private.eu-gb.cloud-object-storage.appdomain.cloud`    |
| EU Germany        | Private | `s3.private.eu-de.cloud-object-storage.appdomain.cloud`    |
| AP Australia      | Private | `s3.private.au-syd.cloud-object-storage.appdomain.cloud`   |
| AP Japan          | Private | `s3.private.jp-tok.cloud-object-storage.appdomain.cloud`   |
{: class="simple-tab-table"}
{: caption="Table 1. Regional Endpoints" caption-side="top"}
{: #regionalendpointtable2}
{: tab-title="Private"}
{: tab-group="Regional-endpoints"}

| Region            | Type   | Endpoint                                                  |
|-------------------|--------|-----------------------------------------------------------|
| US South          | Direct | `s3.direct.us-south.cloud-object-storage.appdomain.cloud` |
| US East           | Direct | `s3.direct.us-east.cloud-object-storage.appdomain.cloud`  |
| EU United Kingdom | Direct | `s3.direct.eu-gb.cloud-object-storage.appdomain.cloud`    |
| EU Germany        | Direct | `s3.direct.eu-de.cloud-object-storage.appdomain.cloud`    |
| AP Australia      | Direct | `s3.direct.au-syd.cloud-object-storage.appdomain.cloud`   |
| AP Japan          | Direct | `s3.direct.jp-tok.cloud-object-storage.appdomain.cloud`   |
{: class="simple-tab-table"}
{: caption="Table 1. Regional Endpoints" caption-side="top"}
{: #regionalendpointtable3}
{: tab-title="Direct"}
{: tab-group="Regional-endpoints"}


## Cross Region Endpoints
{: #endpoints-geo}

Buckets that are created at a cross region endpoint distribute data across three regions. Any one of these regions can suffer an outage or even destruction without impacting availability. Requests are routed to the nearest region's data center by using Border Gateway Protocol (BGP) routing. In an outage, requests are automatically rerouted to an active region. Advanced users who want to write their own failover logic can do so by sending requests to a [specific access point](/docs/services/cloud-object-storage/info?topic=cloud-object-storage-advanced-endpoints) and bypassing the BGP routing.

| Region | Type | Endpoint |
|-----|-----|-----|
| US Cross Region | Public | `s3.us.cloud-object-storage.appdomain.cloud` |
| EU Cross Region | Public | `s3.eu.cloud-object-storage.appdomain.cloud` |
| AP Cross Region | Public | `s3.ap.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 2. Cross Region Endpoints" caption-side="top"}
{: #crossregionalendpointtable1}
{: tab-title="Public"}
{: tab-group="Cross-regional-endpoints"}

| Region | Type | Endpoint |
|-----|-----|-----|
| US Cross Region | Private | `s3.private.us.cloud-object-storage.appdomain.cloud` |
| EU Cross Region | Private | `s3.private.eu.cloud-object-storage.appdomain.cloud` |
| AP Cross Region | Private | `s3.private.ap.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 2. Cross Region Endpoints" caption-side="top"}
{: #crossregionalendpointtable2}
{: tab-title="Private"}
{: tab-group="Cross-regional-endpoints"}

| Region | Type | Endpoint |
|-----|-----|-----|
| US Cross Region | Direct | `s3.direct.us.cloud-object-storage.appdomain.cloud` |
| EU Cross Region | Direct | `s3.direct.eu.cloud-object-storage.appdomain.cloud` |
| AP Cross Region | Direct | `s3.direct.ap.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 2. Cross Region Endpoints" caption-side="top"}
{: #crossregionalendpointtable3}
{: tab-title="Direct"}
{: tab-group="Cross-regional-endpoints"}

## Single Data Center Endpoints
{: #endpoints-zone}

Single data centers are not colocated with IBM Cloud services, such as IAM or Key Protect, and offer no resiliency in a site outage or destruction. 

If a networking failure results in a partition where the data center is unable to access IAM, authentication and authorization information is read from a cache that might become stale. This cached data might result in a lack of enforcement of new or altered IAM policies for up to 24 hours.
{: important}

| Region                      | Type   | Endpoint                                        |
|-----------------------------|--------|-------------------------------------------------|
| Amsterdam, Netherlands      | Public | `s3.ams03.cloud-object-storage.appdomain.cloud` |
| Chennai, India              | Public | `s3.che01.cloud-object-storage.appdomain.cloud` |
| Hong Kong S.A.R. of the PRC | Public | `s3.hkg02.cloud-object-storage.appdomain.cloud` |
| Melbourne, Australia        | Public | `s3.mel01.cloud-object-storage.appdomain.cloud` |
| Mexico City, Mexico         | Public | `s3.mex01.cloud-object-storage.appdomain.cloud` |
| Milan, Italy                | Public | `s3.mil01.cloud-object-storage.appdomain.cloud` |
| Montr&egrave;al, Canada     | Public | `s3.mon01.cloud-object-storage.appdomain.cloud` |
| Oslo, Norway                | Public | `s3.osl01.cloud-object-storage.appdomain.cloud` |
| Paris, France               | Public | `s3.par01.cloud-object-storage.appdomain.cloud` |
| San Jose, US                | Public | `s3.sjc04.cloud-object-storage.appdomain.cloud` |
| S&atilde;o Paulo, Brazil    | Public | `s3.sao01.cloud-object-storage.appdomain.cloud` |
| Seoul, South Korea          | Public | `s3.seo01.cloud-object-storage.appdomain.cloud` |
| Singapore                   | Public | `s3.sng01.cloud-object-storage.appdomain.cloud` |
| Toronto, Canada             | Public | `s3.tor01.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 3. Single Data Center Endpoints" caption-side="top"}
{: #sdcendpointtable1}
{: tab-title="Public"}
{: tab-group="single-datacenter-endpoints"}

| Region                      | Type    | Endpoint                                                |
|-----------------------------|---------|---------------------------------------------------------|
| Amsterdam, Netherlands      | Private | `s3.private.ams03.cloud-object-storage.appdomain.cloud` |
| Chennai, India              | Private | `s3.private.che01.cloud-object-storage.appdomain.cloud` |
| Hong Kong S.A.R. of the PRC | Private | `s3.private.hkg02.cloud-object-storage.appdomain.cloud` |
| Melbourne, Australia        | Private | `s3.private.mel01.cloud-object-storage.appdomain.cloud` |
| Mexico City, Mexico         | Private | `s3.private.mex01.cloud-object-storage.appdomain.cloud` |
| Milan, Italy                | Private | `s3.private.mil01.cloud-object-storage.appdomain.cloud` |
| Montr&egrave;al, Canada     | Private | `s3.private.mon01.cloud-object-storage.appdomain.cloud` |
| Oslo, Norway                | Private | `s3.private.osl01.cloud-object-storage.appdomain.cloud` |
| Paris, France               | Private | `s3.private.par01.cloud-object-storage.appdomain.cloud` |
| San Jose, US                | Private | `s3.private.sjc04.cloud-object-storage.appdomain.cloud` |
| S&atilde;o Paulo, Brazil    | Private | `s3.private.sao01.cloud-object-storage.appdomain.cloud` |
| Seoul, South Korea          | Private | `s3.private.seo01.cloud-object-storage.appdomain.cloud` |
| Singapore                   | Private | `s3.private.sng01.cloud-object-storage.appdomain.cloud` |
| Toronto, Canada             | Private | `s3.private.tor01.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 3. Single Data Center Endpoints" caption-side="top"}
{: #sdcendpointtable2}
{: tab-title="Private"}
{: tab-group="single-datacenter-endpoints"}

| Region                      | Type   | Endpoint                                               |
|-----------------------------|--------|--------------------------------------------------------|
| Amsterdam, Netherlands      | Direct | `s3.direct.ams03.cloud-object-storage.appdomain.cloud` |
| Chennai, India              | Direct | `s3.direct.che01.cloud-object-storage.appdomain.cloud` |
| Hong Kong S.A.R. of the PRC | Direct | `s3.direct.hkg02.cloud-object-storage.appdomain.cloud` |
| Melbourne, Australia        | Direct | `s3.direct.mel01.cloud-object-storage.appdomain.cloud` |
| Mexico City, Mexico         | Direct | `s3.direct.mex01.cloud-object-storage.appdomain.cloud` |
| Milan, Italy                | Direct | `s3.direct.mil01.cloud-object-storage.appdomain.cloud` |
| Montr&egrave;al, Canada     | Direct | `s3.direct.mon01.cloud-object-storage.appdomain.cloud` |
| Oslo, Norway                | Direct | `s3.direct.osl01.cloud-object-storage.appdomain.cloud` |
| Paris, France               | Direct | `s3.direct.par01.cloud-object-storage.appdomain.cloud` |
| San Jose, US                | Direct | `s3.direct.sjc04.cloud-object-storage.appdomain.cloud` |
| S&atilde;o Paulo, Brazil    | Direct | `s3.direct.sao01.cloud-object-storage.appdomain.cloud` |
| Seoul, South Korea          | Direct | `s3.direct.seo01.cloud-object-storage.appdomain.cloud` |
| Singapore                   | Direct | `s3.direct.sng01.cloud-object-storage.appdomain.cloud` |
| Toronto, Canada             | Direct | `s3.direct.tor01.cloud-object-storage.appdomain.cloud` |
{: class="simple-tab-table"}
{: caption="Table 3. Single Data Center Endpoints" caption-side="top"}
{: #sdcendpointtable3}
{: tab-title="Direct"}
{: tab-group="single-datacenter-endpoints"}

## EU-Managed Endpoints
{: #endpoints-eu-managed}

The Activity Tracker and Logging Service with LogDNA can archive to a bucket at specific {{site.data.keyword.cos_full_notm}} instances. This table shows the EU-Managed locations of {{site.data.keyword.cos_short}} instances for archiving events.

| {{site.data.keyword.cos_short}} bucket location | Resiliency   | City                        |
|-------------------------------------------------|--------------|-----------------------------|
| `ams03`                                         | Single Site  | Amsterdam                   |
| `eu-de`                                         | Regional     | Frankfurt                   |
| `eu-gb`                                         | Regional     | London                      |
| `mil01`                                         | Single Site  | Milan                       |
| `osl01`                                         | Single Site  | Oslo                        |
| `par01`                                         | Single Site  | Paris                       |
| `eu-geo`                                        | Cross Region | Amsterdam, Frankfurt, Milan |
{: caption="Table 4. EU-managed Endpoints" caption-side="top"}
 