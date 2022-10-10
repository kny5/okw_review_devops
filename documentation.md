# OKW ERD design

## Introduction:

The OKW Standard it's currently the most used standard of the [IoPA]() with almost 15000 entries
contributed mainly by:

* [Field Ready]()
* [Uganda OSM]() ["IoPA OKW data awards"]()
* [P2P project maker radar]()
* [FabLab network]()

One of the main challenges have been the wrangling and cleaning process of the data contributed.

[null entries in the FR contributed OKW data](assets/images/nulls_fieldready.jpeg)

Part of this issue comes from the missing details of the Data specification. The fields with lesser amount of useful data are the ones related to machines, materials, and processes. During data wrangling the quantity of processes most captured were the simplest ones like sewing but this process without a proper machine described is of poor use for low practical use.

While the take over data from Field Ready and Needs list happened. One of the main issues were to understand the data collected, the purpose of the data itself and how to provide a proper wrangled data that could be usable for them as users and contributors. That raised the question on how to improve clarity in the OKW specification and if there's a need for a boilerplate or template to build up applications that provide a measurable interaction between the data, providers and the use cases.



### Approach on the specification compared to other similar organizations, data models and standards:






### Things missing on the specification that help build a database:

For example (Following Relational Database (SQL) specifications):

* [PRIMARY KEYS]()
* [MANDATORY ATTRIBUTES]()
* [ID ATTRIBUTES]()
* [DATA TYPES]()
* [LONGITUDE OF TEXT ENTRIES]()
* [PRECISION OF DECIMAL NUMBERS]()
* [PRECISION OF FLOATING POINT GPS NUMBERS]()
* [Database formats]()

During the many meetups between the Technology coordinator and the DevOps engineer,
we have the task to develop an ERD design as it's specified in the OKW current version,
a revised version with added missing details and a proposal with changes to the OKW Standard specification.

Points to include in the proposal design:

* OKH and OKW intersection on machine, material and manufacturing process data capture
* Platform agnostic design
* Continuous development of the ERD NS standard specification
* Taking on consideration some real world applications for feedback to achieve improved usability
* Achieve to have a living database and community interaction


### Why:

* Have a usable database
* Review the standard and improve the specification.


### How:

The ERD design process is conducted following this process:
* Reading the OKW specification and write the classes and attributes in the written order.
* Using [DbSchema](link) software to specify the Logical Database Model.
* Write down comments point by point on this document.
* This document is hosted in Github so the review and history of the process is tracked using GIT version control.


## Proposed new attributes

### ID (ATTRIBUTE)

The Identificatory number.

| OKW | Length | 3 Digits Country code (ISO3166) | reviewer_id (Validator) | agent_id (Collector) | project_id |incremental 6 digits integer | Check digit |
|-|-|-|-|-|-|-|-|
|OKW| 23| 484| 00001| 00001| 001| 00001| 1
|OKW| 23| 800| 00010| 00002| 020| 00035|
|OKW| 23| 826| 00023| 00003| 099| 00546|

| Check digit calculation |
|-|
|90:10:0|

|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|4|8|4|0|0|0|0|1|0|0|0|0|1|0|0|1|0|0|0|0|1|
|4|16|12|0|0|0|0|8|0|0|0|0|13|0|0|16|0|0|0|0|21|


SQL Attribute Format:

| Type | Length | Encoding |
|-|-|-|
| VARCHAR | 20 | UTF-8 |


### UUID (ATTRIBUTE)

UUID or “Universally unique identifier” is proposed as part of the meta data. UUID v1 contains the mac address of the machine where the code was generated, and the current date and time.

Example:

ed6c2c50-124b-11ed-9917-479ac5cc5656

These could be useful to track back the databases where the data was first created or incorporated to the IoPA.

Ways to generate UUID v1 ids. (WIP)


# Facilities (CLASS)

Its proposed to have an ID for each "CLASS" so normalization and relationships are possible.

## Name (ATTRIBUTE)

The name given to the facility in the local language.

SQL Attribute Format:

| Type | Length | Encoding |
|-|-|-|
| VARCHAR | 20 | UTF-8 |


## Location (ATTRIBUTE)



## Owner (ATTRIBUTE)

## Contact (ATTRIBUTE)

## AFFILIATION (ATTRIBUTE)

## FACILITY STATUS (ATTRIBUTE)

## OPENING HOURS (ATTRIBUTE)

## DESCRIPTION (ATTRIBUTE)

## DATA FOUNDED (ATTRIBUTE)

## ACCESS TYPE (ATTRIBUTE)

## WHEELCHAIR ACCESSIBILITY (ATTRIBUTE)

## EQUIPMENT (ATTRIBUTE)

## MANUFACTURING PROCESS (ATTRIBUTE)

## TYPICAL BATCH SIZE (ATTRIBUTE)

## SIZE / FLOOR SIZE

## STORAGE CAPACITY ()

## TYPICAL MATERIALS

## CERTIFICATIONS

## BACKUP GENERATOR

## UNINTERRUPTED POWER SUPPLY

## ROAD ACCESS

## LOADING DOCK

## MAINTENANCE SCHEDULE

## TYPICAL PRODUCTS

## PARTNER / FUNDER

## CUSTOMER REVIEWS




# CIRCULAR ECONOMY

## DESCRIPTION


# Notes

## 5.3

Makes a redundant reference to the name property of the agent class.

## 5.8

This mentions images or media of a person, We could define this images as any of the following: logo, brand, icon, gravatar, profile photo, building entry photography or similar.

## 6.

## 6.1

Address is not defined as class or subtype but it has defined sub properties. This is inconsistent compared to the other definitions such as i.e. social_media_subproperties.

## 6.3

There is no mention of the gps_coordinates standard needed, it only mentions "relevant GPS coordinates", GPS refers to Global Positioning System, a governmental radionavigation system. The common way to describe geodesic positioning is EPSG:4326.

## 7.5

This input should consider the capture of scan codes like matrix, qr and barcodes if available.

## 7.6

Since the OKW covers the space, covering the location of the machines seems redundant.

## 7.8

This could be stated as active, inactive, damaged, refurbished, new, modified, stock pieces, and guaranty covered or expired.

## 7.9



## 7.10

Since the OKW covers the space, covering the ownership of the machines seems redundant.

## 7.4

Notes for 7.3 and 7.4 are the same.

## 7.11

This input seems inconsistent with the objective to track each equipment piece. Thus a difference needs to be defined between, machine, power tool, tool, spare part or consumable.

## 7.13

Unit is not specified as Watts only as "W".

## 7.15

Format should be defined as datetime or integer to numerate day periods.

## 7.16

Define units for "usage" like hours a day or hours week, or the average working load or the relative level compared to the other machines in the same facility.

Usage levels should be consider to be renamed or diferenciated from "working cycle". The format for working cycles is: hours or minutes of work / hours or minutes of rest, and cycles per day. i.e. 2h/3h,3



## 7.17

Tolerances using ISO2768 couldn't apply to FDM/SLA/SLS 3D printed parts. Since the referenced standard applies to subtraction manufacturing processes.
