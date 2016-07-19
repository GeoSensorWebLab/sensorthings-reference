# SensorThings API Reference

This reference corresponds to [version 0.9.4 of the OGC SensorThings API document](https://portal.opengeospatial.org/files/?artifact_id=64146) (PDF), dated 2015-06-18. The document is a DRAFT and is not an OGC Standard.

## Introduction

The OGC SensorThings API provides an open and unified way to interconnect Internet of Things devices, data, and applications over the Web. The OGC SensorThings API is an open standard: non-proprietary, platform- independent, and perpetual royalty-free. Although it is a new standard, it builds on a rich set of proven-working and widely-adopted open standards, such as Web protocols and the OGC Sensor Web Enablement (SWE) standards, including the ISO/OGC Observation and Measurement data model [OGC and ISO 19156:2011]. As such, the OGC SensorThings API is extensible and can be applied to both simple and complex use cases.

At a high level, the OGC SensorThings API provides two main functionalities, each handled by a profile. The two profiles are the Sensing profile and the Tasking profile. The Sensing profile provides a standard way to manage and retrieve observations and metadata from heterogeneous IoT sensor systems. This document defines the Sensing profile as Part 1 of the SensorThings API. The Tasking profile provides a standard way for parameterizing - also called tasking - of task-able IoT devices, such as sensors or actuators. The Tasking profile is planned as a future work activity and will be defined in a separate document as Part 2 of the SensorThings API.

The Sensing profile provides functions similar to the OGC Sensor Observation Service (SOS) and the Tasking profile will provide functions similar to the OGC Sensor Planning Service (SPS). The main difference between the SensorThings API and the OGC SOS and SPS is that the SensorThings API is designed specifically for resource-constrained IoT devices and the Web developer community. As a result, the SensorThings API follows REST principles, the use of an efficient JSON encoding, and the use of the flexible OASIS OData protocol and URL conventions.

## 1. Scope

The OGC SensorThings API provides an open standard-based framework to interconnect the Internet of Things devices, data, and applications over the Web.

## 2. Conformance

Conformance with this standard shall be checked using all the relevant tests specified in Annex A (normative), Abstract Test Suite.

The following tables list the requirements classes defined by this standard.

NOTE: The smaller blue text in the following tables is the path fragment that appended to the following URI: http://www.opengis.net/spec/iot_sensing/1.0/, and it provides the URI that can be used to unambiguously identify the requirement and the conformance class.

<table>
  <thead>
    <tr>
      <th>Requirements class id</th>
      <th>Requirements</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>req/entities</td>
      <td>
        <ul>
          <li>req/core/common-control-information</li>
          <li>req/core/thing-properties</li>
          <li>req/core/location-properties</li>
          <li>req/core/historical-location-properties</li>
          <li>req/core/datastream-properties</li>
          <li>req/core/sensor-properties</li>
          <li>req/core/observed-property-properties</li>
          <li>req/core/observation-properties</li>
          <li>req/core/feature-of-interest-properties</li>
          <li>req/core/thing-relations</li>
          <li>req/core/location-relations</li>
          <li>req/core/historical-location-relations</li>
          <li>req/core/datastream-relations</li>
          <li>req/core/sensor-relations</li>
          <li>req/core/observed-property-relations</li>
          <li>req/core/observation-relations</li>
          <li>req/core/feature-of-interest-relations</li>
          <li>req/core/resource-path-to-entities</li>
          <li>req/core/read-entity</li>
        </ul>
      </td>
      <td>Entities of the SensorThings API service and addressing to the entities</td>
    </tr>

    <tr>
      <td>req/request-data</td>
      <td>
        <ul>
          <li>req/request-data/order</li>
          <li>req/request-data/expand</li>
          <li>req/request-data/select</li>
          <li>req/request-data/status-code</li>
          <li>req/request-data/query-status-code</li>
          <li>req/request-data/orderby</li>
          <li>req/request-data/top</li>
          <li>req/request-data/skip</li>
          <li>req/request-data/count</li>
          <li>req/request-data/filter</li>
          <li>req/request-data/built-in-filter-operations</li>
          <li>req/request-data/built-in-filter-functions</li>
          <li>req/request-data/pagination</li>
        </ul>
      </td>
      <td>Requesting data with system query options</td>
    </tr>

    <tr>
      <td>req/create-update-delete</td>
      <td>
        <ul>
          <li>req/create-update-delete/create-entity</li>
          <li>req/create-update-delete/link-to-existing-entities</li>
          <li>req/create-update-delete/deep-insert</li>
          <li>req/create-update-delete/deep-insert-status-code</li>
          <li>req/create-update-delete/update-entity</li>
          <li>req/create-update-delete/delete-entity</li>
          <li>req/historical-location-auto-creation</li>
        </ul>
      </td>
      <td>Creating, updating, and deleting entities</td>
    </tr>

    <tr>
      <td>req/batch-request</td>
      <td>
        <ul>
          <li>req/batch-request/batch-request</li>
        </ul>
      </td>
      <td>Processing multiple requests with a single request</td>
    </tr>

    <tr>
      <td>req/multi-datastream</td>
      <td>
        <ul>
          <li>req/multi-datastream/properties</li>
          <li>req/multi-datastream/relations</li>
          <li>req/multi-datastream/constraints</li>
        </ul>
      </td>
      <td>Handling complex observations with complex results, especially when the result is an array</td>
    </tr>

    <tr>
      <td>req/data-array</td>
      <td>
        <ul>
          <li>req/data-array/data-array</li>
        </ul>
      </td>
      <td>Serving Observations with the efficient data array encoding</td>
    </tr>

    <tr>
      <td>req/mqtt</td>
      <td>
        <ul>
          <li>req/mqtt/create</li>
          <li>req/mqtt/update</li>
          <li>req/mqtt/receive-update</li>
        </ul>
      </td>
      <td>Receiving updates, creating and updating entities through MQTT</td>
    </tr>
  </tbody>
</table>

## 3. Normative References

The following normative documents contain provisions which, through reference in this text, constitute provisions of this document. For dated references, subsequent amendments to, or revisions of, any of these publications do not apply. For undated references, the latest edition of the normative document referred to applies.

* [ISO 8601:1988(E), Data elements and interchange formats – Information interchange - Representation of dates and times.](http://www.iso.org/iso/catalogue_detail.htm?csnumber=15903)
* [OGC and ISO 19156:2011(E), OGC Abstract Specification: Geographic information — Observations and Measurements](http://www.iso.org/iso/catalogue_detail.htm?csnumber=32574)
* [OASIS OData Version 4.0 Part 1: Protocol Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)
* [OASIS OData Version 4.0 Part 2: URL Conventions Plus Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part2-url-conventions.html)
* [OASIS OData JSON Format Version 4.0 Plus Errata 02](http://docs.oasis-open.org/odata/odata-json-format/v4.0/os/odata-json-format-v4.0-os.html)
* [OASIS OData ABNF Construction Rules Errata 02](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/abnf/odata-abnf-construction-rules.txt)
* [RFC 2046, Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types](https://www.ietf.org/rfc/rfc2046.txt)
* [RFC 2616, Hypertext Transfer Protocol -- HTTP/1.1](https://www.ietf.org/rfc/rfc2616.txt)
* [RFC 4627, the application/json Media Type for Javascript Object Notation (JSON), July 2006](https://www.ietf.org/rfc/rfc4627.txt)
* [Unified Code for Units of Measure (UCUM) – Version 1.9, April 2015](http://unitsofmeasure.org/ucum.html)

## 4. Terms and definitions

For the purposes of this document, the following terms and definitions apply:

**Collection**

Sets of Resources, which can be retrieved in whole or in part [RFC5023]

**Entity**

Entities are instances of entity types [OASIS OData Version 4.0 Part 1: Protocol Plus Errata 02]

*Note: Thing, Sensor, Datastream, Observation are some example entity types of the OGC SensorThings API*

**Entity sets**

Entity sets are named collections of entities (e.g. Sensors is an entity set containing Sensor entities). An entity's key uniquely identifies the entity within an entity set. Entity sets provide entry points into an OGC SensorThings API service. [OASIS OData Version 4.0 Part 1: Protocol Plus Errata 02]

**(Internet of) Thing**

A thing is an object of the physical world (physical things) or the information world (virtual things) that is capable of being identified and integrated into communication networks. [ITU-T Y.2060]

**Measurement**

A set of operations having the object of determining the value of a quantity [OGC and ISO 19156:2011]

**Observation**

Act of measuring or otherwise determining the value of a property [OGC and ISO 19156:2011]

**Observation Result**

Estimate of the value of a property determined through a known observation procedure [OGC and ISO 19156:2011]

**Resources**

A network-accessible data object or service identified by an IRI, as defined in [RFC 2616]

**REST**

The Representational State Transfer (REST) style is an abstraction of the architectural elements within a distributed hypermedia system. REST focuses on the roles of components, the constraints upon their interaction with other components, and their interpretation of significant data elements. It encompasses the fundamental constraints upon components, connectors, and data that define the basis of the Web architecture, and thus the essence of its behavior as a network-based application. An API that has REST architecture is called a RESTful API

**Sensor**

An entity capable of observing a phenomenon and returning an observed value. Type of observation procedure that provides the estimated value of an observed property at its output. [OGC 12-000]

## 5. Conventions

### 5.1 Presentation of Requirements and Recommendations

Requirements are presented using the following style:

    Req <number>    <requirement text>
    <requirement id>

`<number>` is a unique number within the document.

`<requirement text>` is the requirement itself. Normative verbs like SHALL are written in capitals.

The text at the bottom of the box `<requirement id>` is the path and it provides the URI of the requirement, which can be used to unambiguously identify the requirement.

Normative verbs like SHALL are written in capitals.

## 6. Symbols (and abbreviated terms)

**API**: Application Programming Interface

**CS-W**: Catalog Service Web

**CRUD**: Create, Read, Update, and Delete

**GML**: Geography Markup Language

**HTML**: HyperText Markup Language

**HTTP**: Hypertext Transfer Protocol

**IoT**: Internet of Things

**ISO**: International Organization for Standardization JSON JavaScript Object Notation

**OData**: the Open Data Protocol

**OGC**: Open Geospatial Consortium OWS OGC Web Services

**O&M**: Observations and Measurements REST REpresentational State Transfer SensorML Sensor Model Language

**SOS**: Sensor Observation Service

**SPS**: Sensor Planning Service

**SWE**: Sensor Web Enablement

**UCUM**: Unified Code for Units of Measure UML Unified Modeling Language

**WoT**: Web of Things

**XML**: eXtensible Markup Language

## 7. SensorThings API overview

### 7.1 Who should use the OGC SensorThings API

Organizations that need a web-based platforms to manage, store, share, analyze IoT-based sensor observation data should use the OGC SensorThings API. The OGC SensorThings API simplifies and accelerates the development of IoT applications. Application developers can use this open standard to connect to various IoT devices and create innovative applications without worrying the daunting heterogeneous protocols of the different IoT devices, gateways and services. IoT device manufacturers can also use OGC SensorThings API as the API can be embedded within various IoT hardware and software platforms, so that the various IoT devices can effortlessly connect with the OGC standard-compliant servers around the world. In summary, the OGC SensorThings API is transforming the numerous disjointed IoT systems into a fully connected platform where complex tasks can be synchronized and performed.

### 7.2 Benefits of the OGC SensorThings API

In today’s world, most IoT devices (e.g., sensors and actuators) have proprietary software interfaces defined by their manufacturers and used selectively. New APIs are often required and developed on an as needed basis, often in an environment with resource limitations and associated risks. This situation requires significant investment on the part of developers for each new sensor or project involving multiple systems and on the part of the providers of sensors, gateways and portals or services where observations and measurements are required.

As a standardized data model and interface for sensors in the WoT and IoT<sup id="a1">[1](#f1)</sup>, the OGC SensorThings API offers the following benefits: (1) it permits the proliferation of new high value services with lower overhead of development and wider reach, (2) it lowers the risks, time and cost across a full IoT product cycle, and (3) it simplifies both devices-to-devices and devices-to-applications.

<strong id="f1">1</strong>: The two terms of IoT and WoT are frequently used interchangeably. [↩](#a1)

## 8. The SensorThings API Sensing Profile Entities

### 8.1 Overview

The OGC SensorThings API data model consists of two parts: (1) the Sensing profile and (2) the Tasking profile. The Sensing profile allows IoT devices and applications to CREATE, READ, UPDATE, and DELETE (i.e., HTTP `POST`, `GET`, `PATCH`, and `DELETE`) IoT data and metadata in a SensorThings service.

Managing and retrieving observations and metadata from IoT sensor systems is one of the most common use cases. As a result, the Sensing profile is designed based on the ISO/OGC Observation and Measurement (O&M) model [OGC and ISO 19156:2011].

The key to the model is that an `Observation` is modeled as an act that produces a result whose value is an estimate of a property of the observation target or `FeatureOfInterest`. An `Observation` instance is classified by its event time (e.g., `resultTime` and `phenonmenonTime`), `FeatureOfInterest`, `ObservedProperty`, and the procedure used (often a `Sensor`).

Moreover, Things are also modeled in the SensorThings API. Further the geographical `Locations` of `Things` are useful in almost every application and as a result are included as well.

In the Sensing profile, a `Thing` has `Locations` and `HistoricalLocations`. A `Thing` also can have multiple `Datastreams`. A `Datastream` is a collection of `Observations` grouped by the same `ObservedProperty` and `Sensor`. An `Observation` is an event performed by a `Sensor` that produces a result whose value is an estimate of an `ObservedProperty` of the `FeatureOfInterest`.

### 8.2 Common Control Information

    Req 1   Each entity SHALL have the following common control information listed in Table 8-1.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/common-control-information

**In SensorThings control information is represented as annotations whose names start with `iot` followed by a dot (.). Annotations are name/value pairs that have a dot (.) as part of the name.**

When annotating a name/value pair for which the value is represented as a JSON object, each annotation is placed within the object and represented as a single name/value pair. In SensorThings the name always starts with the "at" sign (`@`), followed by the namespace `iot`, followed by a dot (.), followed by the name of the term (e.g., "`@iot.id`":`1`).

When annotating a name/value pair for which the value is represented as a JSON array or primitive value, each annotation that applies to this name/value pair is placed next to the annotated name/value pair and represented as a single name/value pair. The name is the same as the name of the name/value pair being annotated, followed by the “at” sign (`@`), followed by the namespace `iot`, followed by a dot (.), followed by the name of the term. (e.g., "`Locations@iot.navigationLink`":"`http://example.org/v.1.0/Things(1)/Locations`")

[Adapted from OData 4.0-JSON-Format section 18]

#### Table 8-1 Common control information

<table>
  <thead>
    <tr>
      <th>Annotation</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td><code>id</code> is the system-generated identifier of an entity. <code>id</code> is unique among the entities of the same entity type in a SensorThings service.</td>
      <td>Any</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>selfLink</code></td>
      <td><code>selfLink</code> is the absolute URL of an entity that is unique among all other entities.</td>
      <td>URL</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>navigationLink</code></td>
      <td><code>navigationLink</code> is the relative URL that retrieves content of related entities.</td>
      <td>Relative URL</td>
      <td>One-to-many (mandatory)</td>
    </tr>
  </tbody>
</table>

### 8.3 The Sensing Profile Core Entities

The SensorThings API Sensing Profile Core Entities are depicted in Figure 1.

![Sensing Profile Core Entities](images/figure-1-core-entities.png)

**Figure 1 Sensing Profile Core Entities**

In this section, we explain the properties in each entity type and the direct relation to the other entity types. In addition, for each entity type, we show an example of the associated JSON encoding.

### 8.3.1 `Thing`

The OGC SensorThings API follows the ITU-T definition, *i.e.*, with regard to the Internet of Things, a thing is an object of the physical world (physical things) or the information world (virtual things) that is capable of being identified and integrated into communication networks [ITU-T Y.2060].

    Req 2   Each Thing entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-2.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/thing-properties

#### Table 8-2 Properties of a `Thing` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>description</code></td>
      <td>This is a short description of the corresponding <code>Thing</code> entity.</td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>properties</code></td>
      <td>A JSON Object containing user-annotated properties as key-value pairs.</td>
      <td>JSON Object</td>
      <td>Zero-to-one</td>
    </tr>
  </tbody>
</table>

    Req 3   Each Thing entity SHALL have the direct relation between a Thing entity and other entity types listed in Table 8-3.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/thing-relations

#### Table 8-3 Direct relation between a `Thing` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Location</code></td>
      <td>Many optional to many optional</td>
      <td>
        <p>
          The <code>Location</code> entity locates the <code>Thing</code>. Multiple <code>Things</code> MAY be located at the same <code>Location</code>. A <code>Thing</code> MAY not have a <code>Location</code>. A <code>Thing</code> SHOULD have only one <code>Location</code>.
        </p>
        <p>
          However, in some complex use cases, a <code>Thing</code> MAY have more than one <code>Location</code> representations. In such case, the <code>Thing</code> MAY have more than one <code>Locations</code>. These <code>Locations</code> SHALL have different <code>encodingTypes</code> and the <code>encodingTypes</code> SHOULD be in different spaces (e.g., one <code>encodingType</code> in Geometrical space and one <code>encodingType</code> in Topological space).
        </p>
      </td>
    </tr>

    <tr>
      <td><code>HistoricalLocation</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          A <code>Thing</code> has zero-to-many <code>HistoricalLocations</code>. A <code>HistoricalLocation</code> has one-and-only-one <code>Thing</code>
        </p>
      </td>
    </tr>

    <tr>
      <td><code>Datastream</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          A <code>Thing</code> MAY have zero-to-many <code>Datastreams</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 1 an example of a `Thing` entity:


```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/Things(1)",
  "Locations@iot.navigationLink": "Things(1)/Locations",
  "Datastreams@iot.navigationLink": "Things(1)/Datastreams",
  "HistoricalLocations@iot.navigationLink": "Things(1)/HistoricalLocations",
  "description": "This thing is an oven.",
  "properties": {
    "owner": "John Doe",
    "color": "Silver"
  }
}
```

### 8.3.2 `Location`

The `Location` entity locates the `Thing` or the `Things` it associated with. A Thing’s `Location` entity is
defined as the last known location of the `Thing`.

A `Thing`’s `Location` may be identical to the `Thing`’s `Observations’` `FeatureOfInterest`. In the context of the IoT, the principle location of interest is usually associated with the location of the `Thing`, especially for in-situ sensing applications. For example, the location of interest of a wifi-connected thermostat should be the building or the room in which the smart thermostat is located. And the `FeatureOfInterest` of the `Observations` made by the thermostat (e.g., room temperature readings) should also be the building or the room. In this case, the content of the smart thermostat’s location should be the same as the content of the temperature readings’ feature of interest.

However, the ultimate location of interest of a `Thing` is not always the location of the `Thing` (e.g., in the case of remote sensing). In those use cases, the content of a `Thing`’s `Location` is different from the content of the `FeatureOfInterest` of the `Thing`’s `Observations`. Section 7.1.4 of [OGC and ISO 19156:2011] provides a detailed explanation of observation location.

    Req 4    Each Location entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-4.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/location-properties

#### Table 8-4 Properties of a `Location` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>description</code></td>
      <td>The description about the <code>Location</code>.</td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>encodingType</code></td>
      <td>The encoding type of the <code>location</code> property. Its value is one of the ValueCode enumeration (see Table 8-6).</td>
      <td>ValueCode</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>location</code></td>
      <td>The <code>location</code> type is defined by <code>encodingType</code>.</td>
      <td>Any (<em>i.e.</em>, the type is depending on the value of the <code>encodingType</code>)</td>
      <td>One (mandatory)</td>
    </tr>
  </tbody>
</table>

    Req 5     Each Location entity SHALL have the direct relation between a Location entity and other entity types listed in Table 8-5.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/location-relations

#### Table 8-5 Direct relation between a `Location` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Thing</code></td>
      <td>Many optional to many optional</td>
      <td>
        <p>
          Multiple <code>Things</code> MAY locate at the same <code>Location</code>. A <code>Thing</code> MAY not have a <code>Location</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>HistoricalLocation</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          A <code>Location</code> can have zero-to-many <code>HistoricalLocations</code>. One <code>HistoricalLocation</code> SHALL have one or many <code>Locations</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 2 an example of a `Location` entity:

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/Locations(1)",
  "Things@iot.navigationLink": "Locations(1)/Things",
  "HistoricalLocations@iot.navigationLink": "Locations(1)/HistoricalLocations",
  "encodingType": "application/vnd.geo+json",
  "location": {
    "type": "Point",
    "coordinates": [
      -114.06,
      51.05
    ]
  }
}
```

#### Table 8-6 List of some code values used for identifying types for the `encodingType` of the `Location` and `FeatureOfInterest` entity

<table>
  <thead>
    <tr>
      <th>Location <code>encodingType</code></th>
      <th>ValueCode Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>GeoJSON</td>
      <td>application/vnd.geo+json</td>
    </tr>
  </tbody>
</table>

### 8.3.3 `HistoricalLocation`

A `Thing`’s `HistoricalLocation` entity set provides the current (*i.e.*, last known) and previous locations of the `Thing` with their time.


    Req 6     Each HistoricalLocation entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-7.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/historical-location-properties

    Req 7     Each HistoricalLocation entity SHALL have the direct relation between a Location entity and other entity types listed in Table 8-8.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/historical-location-relations

    Req 8     When a Thing has a new Location, a new HistoricalLocation SHALL be created and added to the Thing automatically by the service. The current Location of the Thing SHALL only be added to HistoricalLocation automatically by the service, and SHALL not be created as HistoricalLocation directly by user.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/historical-location-auto-creation

The `HistoricalLocation` can also be created, updated and deleted. One use case is to migrate historical observation data from an existing observation data management system to a SensorThings API system.

#### Table 8-7 Properties of an `HistoricalLocation` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>time</code></td>
      <td>The time when the <code>Thing</code> is known at the <code>Location</code>.</td>
      <td>TM_Instant (ISO-8601 Time String)</td>
      <td>One (mandatory)</td>
    </tr>
  </tbody>
</table>

#### Table 8-8 Direct relation between an `HistoricalLocation` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Location</code></td>
      <td>Many optional to many mandatory</td>
      <td>
        <p>
          A <code>Location</code> can have zero-to-many <code>HistoricalLocations</code>. One <code>HistoricalLocation</code> SHALL have one or many <code>Locations</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>Thing</code></td>
      <td>Many optional to many mandatory</td>
      <td>
        <p>
          A <code>HistoricalLocation</code> has one-and-only-one <code>Thing</code>. One <code>Thing</code> MAY have zero-to-many <code>HistoricalLocations</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 3 An example of a `HistoricalLocations` entity set (e.g., `Things(1)/HistoricalLocations`):

```json
{
  "value": [
    {
      "@iot.id": 1,
      "@iot.selfLink": "http://example.org/v1.0/HistoricalLocations(1)",
      "Locations@iot.navigationLink": "HistoricalLocations(1)/Locations",
      "Thing@iot.navigationLink": "HistoricalLocations(1)/Thing",
      "time": "2015-01-25T12:00:00-07:00"
    },
    {
      "@iot.id": 1,
      "@iot.selfLink": "http://example.org/v1.0/HistoricalLocations(2)",
      "Locations@iot.navigationLink": "HistoricalLocations(2)/Locations",
      "Thing@iot.navigationLink": "HistoricalLocations(2)/Thing",
      "time": "2015-01-25T13:00:00-07:00"
    }
  ],
  "@iot.nextLink": "http://example.org/v1.0/Things(1)/HistoricalLocations?$skip=2&$top=2"
}
```

### 8.3.4 `Datastream`

A `Datastream` groups a collection of `Observations` and the `Observations` in a `Datastream` measure the
same `ObservedProperty` and are produced by the same `Sensor`.

    Req 9     Each Datastream entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-9.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/datastream-properties

    Req 10    Each Datastream entity SHALL have the direct relation between a Datastream entity and other entity types listed in Table 8-10.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/datastream-relations

#### Table 8-7 Properties of a `Datastream` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>description</code></td>
      <td>
        The description of the <code>Datastream</code> entity.
      </td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>unitOfMeasurement</code></td>
      <td>
        <p>
          A JSON Object containing three key-value pairs. The name property presents the full name of the <code>unitOfMeasurement</code>; the <code>symbol</code> property shows the textual form of the unit symbol; and the <code>definition</code> contains the IRI defining the <code>unitOfMeasurement</code>.
        </p>
        <p>
          The values of these properties SHOULD follow the Unified Code for Unit of Measure (UCUM).
        </p>
      </td>
      <td>JSON Object</td>
      <td>
        <p>One (mandatory)</p>
        <p>
          Note: When a <code>Datastream</code> does not have a unit of measurement (e.g., a <code>OM_TruthObservation</code> type), the corresponding <code>unitOfMeasurement</code> properties SHALL have <code>null</code> values.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>observationType</code></td>
      <td>
        The type of <code>Observation</code> (with unique result type), which is used by the service to encode observations.
      </td>
      <td>ValueCode<br>
      see Table 8-10.</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>observedArea</code></td>
      <td>
        The spatial bounding box of the spatial extent of all <code>FeaturesOfInterest</code> that belong to the <code>Observations</code> associated with this <code>Datastream</code>.
      </td>
      <td>GM_Envelope (GeoJSON Polygon)</td>
      <td>Zero-to-one</td>
    </tr>

    <tr>
      <td><code>phenomenonTime</code></td>
      <td>
        The temporal bounding box of the phenomenon times of all observations belonging to this <code>Datastream</code>.
      </td>
      <td>TM_Period (ISO 8601 Time Interval)</td>
      <td>Zero-to-one</td>
    </tr>

    <tr>
      <td><code>resultTime</code></td>
      <td>
        The temporal bounding box of the result times of all observations belonging to this <code>Datastream</code>.
      </td>
      <td>TM_Period (ISO 8601 Time Interval)</td>
      <td>Zero-to-one</td>
    </tr>
  </tbody>
</table>

#### Table 8-10 Direct relation between a `Datastream` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Thing</code></td>
      <td>Many optional to one mandatory</td>
      <td>
        <p>
          A <code>Thing</code> has zero-to-many <code>Datastreams</code>. A <code>Datastream</code> entity SHALL only link to a <code>Thing</code> as a collection of <code>Observations</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>Sensor</code></td>
      <td>Many optional to one mandatory</td>
      <td>
        <p>
          The <code>Observations</code> in a <code>Datastream</code> are performed by one-and-only-one <code>Sensor</code>. One <code>Sensor</code> MAY produce zero-to-many <code>Observations</code> in different <code>Datastreams</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>ObservedProperty</code></td>
      <td>Many optional to one mandatory</td>
      <td>
        <p>
          The <code>Observations</code> of a <code>Datastream</code> SHALL observe the same <code>ObservedProperty</code>. The <code>Observations</code> of different <code>Datastreams</code> MAY observe the same <code>ObservedProperty</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>Observation</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          A <code>Datastream</code> has zero-to-many <code>Observations</code>. One <code>Observation</code> SHALL occur in one-and-only-one <code>Datastream</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 4 A `Datastream` entity example:

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/Datastreams(1)",
  "Thing@iot.navigationLink": "HistoricalLocations(1)/Thing",
  "Sensor@iot.navigationLink": "Datastreams(1)/Sensor",
  "ObservedProperty@iot.navigationLink": "Datastreams(1)/ObservedProperty",
  "Observations@iot.navigationLink": "Datastreams(1)/Observations",
  "description": "This is a datastream measuring the temperature in an oven.",
  "unitOfMeasurement": {
    "name": "degree Celsius",
    "symbol": "°C",
    "definition": "http://unitsofmeasure.org/ucum.html#para-30"
  },
  "observationType": "http://www.opengis.net/def/observationType/OGC- OM/2.0/OM_Measurement",
  "observedArea": {
    "type": "Polygon",
    "coordinates": [
      [
        [
          100,
          0
        ],
        [
          101,
          0
        ],
        [
          101,
          1
        ],
        [
          100,
          1
        ],
        [
          100,
          0
        ]
      ]
    ]
  },
  "phenomenonTime": "2014-03-01T13:00:00Z/2015-05-11T15:30:00Z",
  "resultTime": "2014-03-01T13:00:00Z/2015-05-11T15:30:00Z"
}
```

The `observationType` defines the result types for specialized observations [OGC and ISO 19156:2011 Table 3]. The following table shows some of the `valueCodes` that maps the UML classes in O&M v2.0 [OGC and ISO 19156:2011] to `observationType` names and `observation` result types.

#### Table 8-11 List of some code values used for identifying types defined in the O&M conceptual model (OGC and ISO 19156:2011)

<table>
  <thead>
    <tr>
      <th>O&amp;M 2.0</th>
      <th>Value Code Value (<code>observationType</code> names)</th>
      <th>Content of <code>result</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>OM_CategoryObservation</td>
      <td><code>http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_CategoryObservation</code></td>
      <td>IRI</td>
    </tr>

    <tr>
      <td>OM_CountObservation</td>
      <td><code>http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_CountObservation</code></td>
      <td>integer</td>
    </tr>

    <tr>
      <td>OM_Measurement</td>
      <td><code>http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement</code></td>
      <td>double</td>
    </tr>

    <tr>
      <td>OM_Observation</td>
      <td><code>http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Observation</code></td>
      <td>Any</td>
    </tr>

    <tr>
      <td>OM_TruthObservation</td>
      <td><code>http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_TruthObservation</code></td>
      <td>boolean</td>
    </tr>
  </tbody>
</table>

### 8.3.5 `Sensor`

A `Sensor` is an instrument that observes a property or phenomenon with the goal of producing an estimate of the
value of the property<sup id="a2">[2](#f2)</sup>.

    Req 8 Each Sensor entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-12.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/sensor-properties

    Req 9 Each Sensor entity SHALL have the direct relation between a Sensor entity and other entity types listed in Table 8-13.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/sensor-relations

<strong id="f2">2</strong>: In some cases, the `Sensor` in this data model can also be seen as the `Procedure` (method, algorithm, or instrument) defined in [OGC and ISO 19156:2011]. [↩](#a2)

#### Table 8-12 Properties of a `Sensor` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>description</code></td>
      <td>
        The description of the <code>Sensor</code> entity.
      </td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>encodingType</code></td>
      <td>
        <p>
          The encoding type of the <code>metadata</code> property. Its value is one of the ValueCode enumeration (see Table 8-14 for the available ValueCode).
        </p>
      </td>
      <td>ValueCode</td>
      <td>
        <p>One (mandatory)</p>
      </td>
    </tr>

    <tr>
      <td><code>metadata</code></td>
      <td>
        The detailed description of the <code>Sensor</code> or system. The metadata type is defined by <code>encodingType</code>.
      </td>
      <td>ValueCode<br>
      see Table 8-10.</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>observedArea</code></td>
      <td>
        The spatial bounding box of the spatial extent of all <code>FeaturesOfInterest</code> that belong to the <code>Observations</code> associated with this <code>Datastream</code>.
      </td>
      <td>Any (depending on the value of the <code>encodingType</code>)</td>
      <td>One (mandatory)</td>
    </tr>
  </tbody>
</table>

#### Table 8-13 Direct relation between a `Sensor` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Datastream</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          The <code>Observations</code> of a <code>Datastream</code> are measured with the same <code>Sensor</code>. One <code>Sensor</code> MAY produce zero-to-many <code>Observations</code> in different <code>Datastreams</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Table 8-14 List of some code values used for identifying types for the `encodingType` of the `Sensor` entity

<table>
  <thead>
    <tr>
      <th><code>Sensor encodingType</code></th>
      <th>Value Code Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>PDF</td>
      <td><code>application/pdf</code></td>
    </tr>

    <tr>
      <td>SensorML</td>
      <td><code>http://www.opengis.net/doc/IS/SensorML/2.0</code></td>
    </tr>
  </tbody>
</table>

#### Example 5 An example of a `Sensor` entity:

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/Sensors(1)",
  "Datastreams@iot.navigationLink": "Sensors(1)/Datastreams",
  "description": "TMP36 - Analog Temperature sensor",
  "encodingType": "application/pdf",
  "metadata": "http://example.org/TMP35_36_37.pdf"
}
```

### 8.3.6 `ObservedProperty`

An `ObservedProperty` specifies the phenomenon of an `Observation`.

    Req 10    Each ObservedProperty entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-15.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/observed-property-properties

    Req 11    Each ObservedProperty entity SHALL have the direct relation between a ObservedProperty entity and other entity types listed in Table 8-16.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/observed-property-relations

#### Table 8-15 Properties of an `ObservedProperty` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>name</code></td>
      <td>
        The name of the <code>ObservedProperty</code>.
      </td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>definition</code></td>
      <td>
        <p>
          The IRI of the <code>ObservedProperty</code>. Dereferencing this IRI SHOULD result in a representation of the definition of the <code>ObservedProperty</code>.
        </p>
      </td>
      <td>IRI</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>description</code></td>
      <td>
        A description about the <code>ObservedProperty</code>.
      </td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>
  </tbody>
</table>

#### Table 8-16 Direct relation between an `ObservedProperty` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Datastream</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          The <code>Observations</code> of a <code>Datastream</code> observe the same <code>ObservedProperty</code>. The <code>Observations</code> of different <code>Datastreams</code> MAY observe the same <code>ObservedProperty</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 6 an example `ObservedProperty` entity:

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/ObservedProperties(1)",
  "Datastreams@iot.navigationLink": "ObservedProperties(1)/Datastreams",
  "description": "The dewpoint temperature is the temperature to which the air mustbe cooled, at constant pressure, for dew to form. As the grass and other objects near the ground cool to the dewpoint, some of the water vapor in the atmosphere condenses into liquid water on the objects.",
  "name": "DewPoint Temperature",
  "definition": "http://dbpedia.org/page/Dew_point"
}
```

### 8.3.7 `Observation`

An `Observation` is act of measuring or otherwise determining the value of a property [OGC and ISO
19156:2011]

    Req 12    Each Observation entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-17.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/observation-properties

    Req 13    Each Observation entity SHALL have the direct relation between an Observation entity and other entity types listed in Table 8-18.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/observation-relations

#### Table 8-17 Properties of an `Observation` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>phenomenonTime</code></td>
      <td>
        <p>
          The time instant or period of when the <code>Observation</code> happens.
        </p>
        <p>
          Note: Many resource-constrained sensing devices do not have a clock. As a result, a client may omit <code>phenonmenonTime</code> when <code>POST</code> new <code>Observations</code>, even though <code>phenonmenonTime</code> is a mandatory property. When a SensorThings service receives a <code>POST Observations</code> without <code>phenonmenonTime</code>, the service SHALL assign the current server time to the value of the <code>phenomenonTime</code>.
        </p>
      </td>
      <td>TM_Object (ISO 8601 Time string or Time Interval string (e.g., <code>2010-12-23T10:20:00.00-07:00</code> or <code>2010-12-23T10:20:00.00-07:00/2010-12-23T12:20:00.00-07:00</code>))</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>result</code></td>
      <td>
        <p>
          The estimated value of an <code>ObservedProperty</code> from the <code>Observation</code>.
        </p>
      </td>
      <td>Any (depends on the <code>observationType</code> defined in the associated <code>Datastream</code>)</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>resultTime</code></td>
      <td>
        <p>
          The time of the Observation's result was generated.
        </p>
        <p>
          Note: Many resource-constrained sensing devices do not have a clock. As a result, a client may omit <code>resultTime</code> when <code>POST</code> new <code>Observations</code>, even though <code>resultTime</code> is a mandatory property. When a SensorThings service receives a <code>POST Observations</code> without <code>resultTime</code>, the service SHALL assign a null value to the <code>resultTime</code>.
        </p>
      </td>
      <td>TM_Instant (ISO 8601 Time string)</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>resultQuality</code></td>
      <td>
        <p>
          Describes the quality of the <code>result</code>.
        </p>
      </td>
      <td>DQ_Element</td>
      <td>Zero-to-many</td>
    </tr>

    <tr>
      <td><code>validTime</code></td>
      <td>
        <p>
          The time period during which the <code>result</code> may be used.
        </p>
      </td>
      <td>TM_Period (ISO 8601 Time Interval string)</td>
      <td>Zero-to-one</td>
    </tr>

    <tr>
      <td><code>parameters</code></td>
      <td>
        <p>
          Key-value pairs showing the environmental conditions during measurement.
        </p>
      </td>
      <td>NamedValues in a JSON Array</td>
      <td>Zero-to-one</td>
    </tr>
  </tbody>
</table>

#### Table 8-18 Direct relation between an `Observation` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Datastream</code></td>
      <td>Many optional to one mandatory</td>
      <td>
        <p>
          A <code>Datastream</code> can have zero-to-many <code>Observations</code>. One <code>Observation</code> SHALL occur in one-and-only-one <code>Datastream</code>.
        </p>
      </td>
    </tr>

    <tr>
      <td><code>FeatureOfInterest</code></td>
      <td>Many optional to one mandatory</td>
      <td>
        <p>
          An <code>Observation</code> observes on one-and-only-one <code>FeatureOfInterest</code>. One <code>FeatureOfInterest</code> could be observed by zero-to-many <code>Observations</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 7 An `Observation` entity example

The following example shows an `Observation` whose `Datastream` has an `ObservationType` of `OM_Measurement`. A `result`’s data type is defined by the `observationType`.

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/Observations(1)",
  "FeatureOfInterest@iot.navigationLink": "Observations(1)/FeatureOfInterest",
  "Datastream@iot.navigationLink": "Observations(1)/Datastream",
  "phenomenonTime": "2014-12-31T11:59:59.00+08:00",
  "resultTime": "2014-12-31T11:59:59.00+08:00",
  "result": 70.4
}
```

### 8.3.8 `FeatureOfInterest`

An `Observation` results in a value being assigned to a phenomenon. The phenomenon is a property of a feature, the latter being the `FeatureOfInterest` of the `Observation` [OGC and ISO 19156:2001]. In the context of the Internet of Things, many `Observations`’ `FeatureOfInterest` can be the `Location` of the `Thing`. For example, the `FeatureOfInterest` of a wifi-connect thermostat can be the `Location` of the thermostat (i.e., the living room where the thermostat is located in). In the case of remote sensing, the `FeatureOfInterest` can be the geographical area or volume that is being sensed.

    Req 14    Each FeatureOfInterest entity SHALL have the mandatory properties and MAY have the optional properties listed in Table 8-19.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/feature-of-interest-properties

    Req 15    Each FeatureOfInterest entity SHALL have the direct relation between a FeatureOfInterest entity and other entity types listed in Table 8-20.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/feature-of-interest-relations

#### Table 8-19 Properties of a `FeatureOfInterest` entity

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Definition</th>
      <th>Data Type</th>
      <th>Multiplicity and use</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>description</code></td>
      <td>
        <p>
          The description about the <code>FeatureOfInterest</code>.
        </p>
      </td>
      <td>Character String</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>encodingType</code></td>
      <td>
        <p>
          The encoding type of the feature property. Its value is one of the ValueCode enumeration (see Table 8-6 for the available ValueCode).
        </p>
      </td>
      <td>ValueCode</td>
      <td>One (mandatory)</td>
    </tr>

    <tr>
      <td><code>feature</code></td>
      <td>
        <p>
          The detailed description of the feature. The data type is defined by <code>encodingType</code>.
        </p>
      </td>
      <td>Any</td>
      <td>One (mandatory)</td>
    </tr>
  </tbody>
</table>

#### Table 8-20 Direct relation between a `FeatureOfInterest` entity and other entity types

<table>
  <thead>
    <tr>
      <th>Entity Type</th>
      <th>Relation</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>Observation</code></td>
      <td>One mandatory to many optional</td>
      <td>
        <p>
          An <code>Observation</code> observes on one-and-only-one <code>FeatureOfInterest</code>. One <code>FeatureOfInterest</code> could be observed by zero-to-many <code>Observations</code>.
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Example 8 an example of a `FeatureOfInterest` entity

```json
{
  "@iot.id": 1,
  "@iot.selfLink": "http://example.org/v1.0/FeaturesOfInterest(1)",
  "Observations@iot.navigationLink": "FeaturesOfInterest(1)/Observations",
  "description": "This is a weather station.",
  "encodingType": "application/vnd.geo+json",
  "feature": {
    "type": "Point",
    "coordinates": [
      -114.06,
      51.05
    ]
  }
}
```

## 9. SensorThings Service Interface

An OGC SensorThings API service exposes a service document resources that describe its data model. The service document lists the entity sets that can be CRUD. SensorThings API clients can use the service document to navigate the available entities in a hypermedia-driven fashion.

### 9.1 URI Components

The OGC SensorThings API service groups the same types of entities into *entity sets*. Each entity has a unique identifier and one-to-many properties. Also, in the case of an entity holding a relationship with entities in other entity sets, this type of relationship is expressed with navigation properties (i.e., `navigationLink` and `associationLink`).

Therefore, in order to perform CRUD action on the resources, the first step is to address to the target resource(s) through URI. There are three major URI components used here, namely (1) *the service root URI*, (2) the *resource path*, and (3) the *query options*. In addition, the service root URI consists of two parts: (1) the location of the SensorThings service and (2) the version number. The version number follows the format indicated below:

    "v"majorversionnumber + "." + minorversionnumber

#### Example 9 complete URI example

    http://example.org/v1.0/Observations?$orderby=ID&$top=10
    _______________________|____________|___________________|
              |                   |               |
      service root URI      resource path   query options

By attaching the resource path after the service root URI, clients can address to different types of resources such as an entity set, *an entity*, *a property*, or *a navigation property*. Finally, clients can apply query options after the resource path to further process the addressed resources, such as sorting by properties or filtering with criteria.

### 9.2 Resource Path

The resource path comes right after the service root URI and can be used to address to different resources. The following lists the usages of the resource path.

    Req 16    An OGC SensorThings API service SHALL support all the resource path usages listed in Section 9.2.
    http://www.opengis.net/spec/iot_sensing/1.0/req/core/resource-path-to-entities

#### 9.2.1 Usage 1: no resource path

**URI Pattern:** `SERVICE_ROOT_URI`

**Response:** A JSON object with a property named `value`. The value of the property SHALL be a JSON Array containing one element for each entity set of the SensorThings Service.

Each element SHALL be a JSON object with at least two name/value pairs, one with name name containing the name of the entity set (e.g., `Things`, `Locations`, `Datastreams`, `Observations`, `ObservedProperties` and `Sensors`) and one with name `url` containing the URL of the entity set, which may be an absolute or a relative URL.

[Adapted from OData 4.0-JSON-Format section 5]

#### Example 10 a SensorThings request with no resource path

**Example Request:** `http://example.org/v1.0/`

**Example Response:**

```json
{
  "value": [
    {
      "name": "Things",
      "url": "http://example.org/v1.0/Things"
    },
    {
      "name": "Locations",
      "url": " http://example.org/v1.0/Locations"
    },
    {
      "name": "Datastreams",
      "url": " http://example.org/v1.0/Datastreams"
    },
    {
      "name": "Sensors",
      "url": " http://example.org/v1.0/Sensors"
    },
    {
      "name": "Observations",
      "url": " http://example.org/v1.0/Observations"
    },
    {
      "name": "ObservedProperties",
      "url": " http://example.org/v1.0/ObservedProperties"
    },
    {
      "name": "FeaturesOfInterest",
      "url": " http://example.org/v1.0/FeaturesOfInterest"
    }
  ]
}
```

#### 9.2.2 Usage 2: address to a collection of entities

To address to an entity set, users can simply put the entity set name after the service root URI. The service returns a JSON object with a property of value. The value of the property SHALL be a list of the entities in the specified entity set.

**URI Pattern:** `SERVICE_ROOT_URI/ENTITY_SET_NAME`

**Response:** A list of all entities (with all the properties) in the specified entity set when there is no service-driven pagination imposed. The response is represented as a JSON object containing a name/value pair named `value`. The value of the `value` name/value pair is a JSON array where each element is representation of an entity or a representation of an entity reference. An empty collection is represented as an empty JSON array.

The `count` annotation represents the number of entities in the collection. If present, it comes before the `value` name/value pair.

When there is service-driven pagination imposed, the `nextLink` annotation is included in a response that represents a partial result.

[Adapted from OData 4.0-JSON-Format section 12]

#### Example 11 an example to address an entity set

**Example Request:** `http://example.org/v1.0/ObservedProperties`

**Example Response:**

```json
{
  "@iot.count": 84,
  "value": [
    {
      "@iot.id": 1,
      "@iot.selfLink": "http://example.org/v1.0/ObservedProperties(1)",
      "Datastreams@iot.navigationLink": "ObservedProperties(1)/Datastreams",
      "description": "The dew point is the temperature at which the water vapor in air at constant barometric pressure condenses into liquid water at the same rate at which it evaporates.",
      "name": "DewPoint Temperature",
      "definition": "http://dbpedia.org/page/Dew_point"
    },
    {
      "@iot.id ": 2,
      "@iot.selfLink": "http://example.org/v1.0/ObservedProperties(2)",
      "Datastreams@iot.navigationLink": "ObservedProperties(2)/Datastreams",
      "description": "Relative humidity is the ratio of the partial pressure of water vapor in an air-water mixture to the saturated vapor pressure of water at a prescribed temperature.",
      "name": "Relative Humidity",
      "definition": "http://dbpedia.org/page/Relative_humidity"
    },
    // Addition entities omitted for example
  ],
  "@iot.nextLink": "http://example.org/v1.0/ObservedProperties?$top=5&$skip=5"
}
```

#### 9.2.3 Usage 3: address to an entity in a collection

Users can address to a specific entity in an entity set by place the unique identifier of the entity between brace symbol "()" and put after the entity set name. The service then returns the entity with all its properties.

**URI Pattern:** `SERVICE_ROOT_URI/ENTITY_SET_NAME(ID_OF_THE_ENTITY)`

**Response:** A JSON object of the entity (with all its properties) that holds the specified id in the entity set.

#### Example 12: an example request that addresses to an entity in a collection

**Example Request:** `http://example.org/v1.0/ObservedProperties`

#### 9.2.4 Usage 4: address to a property of an entity

Users can address to a property of an entity by specifying the property name after the URI addressing to the entity. The service then returns the value of the specified property. If the property has a complex type value, properties of that value can be addressed by further property name composition.

If the property is single-valued and has the `null` value, the service SHALL respond with `204 No Content`. If the property is not available, for example due to permissions, the service SHALL respond with `404 Not Found`.

[Adapted from OData 4.0-Protocol 11.2.3]

**URI Pattern:** `SERVICE_ROOT_URI/RESOURCE_PATH_TO_AN_ENTITY/PROPERTY_NAME`

**Response:** The specified property of an entity that holds the `id` in the entity set.

#### Example 13: an example to address to a property of an entity

**Example Request:** `http://example.org/v1.0/Observations(1)/resultTime`

**Example Response:**

```json
{
  "resultTime": "2010-12-23T10:20:00-07:00"
}
```

#### 9.2.5 Usage 5: address to the value of an entity’s property

To address the raw value of a primitive property, clients append a path segment containing the string `$value` to the property URL.

The default format for `TM_Object` types is `text/plain` using the ISO8601 format, such as `2014-03- 01T13:00:00Z/2015-05-11T15:30:00Z` for `TM_Period` and `2014-03-01T13:00:00Z` for `TM_Instant`.

**URI Pattern:** `SERVICE_ROOT_URI/ENTITY_SET_NAME(ID_OF_THE_ENTITY)/PROPERTY_NAME/$value`

**Response:** The raw value of the specified property of an entity that holds the `id` in the entity set.

#### Example 14: an example of addressing to the value of an entity’s property

**Example Request:** `http://example.org/v1.0/Observations(1)/resultTime/$value`

**Example Response:**

    2015-01-12T23:00:13-07:00

#### 9.2.6 Usage 6: address to a navigation property (`navigationLink`)

As the entities in different entity sets may hold some relationships, users can request the linked entities by addressing to a navigation property of an entity. The service then returns one or many entities that hold a certain relationship with the specified entity.

**URI Pattern:** `SERVICE_ROOT_URI/ENTITY_SET_NAME(ID_OF_THE_ENTITY)/LINK_NAME`

**Response:** A JSON object of one entity or a JSON array of many entities that holds a certain relationship with the specified entity.

#### Example 15: an example request addressing to a navigational property

**Example:** `http://example.org/v1.0/Datastreams(1)/Observations` returns all the `Observations` in
the `Datastream` that holds the `id` 1.

#### 9.2.7 Usage 7: address to an `associationLink`

As the entities in different entity sets may hold some relationships, users can request the linked entities’ `selfLinks` by addressing to an association link of an entity. An `associationLink` can be used to retrieve a reference to an entity or an entity set related to the current entity. Only the `selfLinks` of related entities are returned when resolving `associationLinks`.

**URI Pattern:** `SERVICE_ROOT_URI/ENTITY_SET_NAME(KEY_OF_THE_ENTITY)/LINK_NAME/$ref`

**Response:** A JSON object with a `value` property. The value of the `value` property is a JSON array containing one element for each `associationLink`. Each element is a JSON object with a name/value pairs. The name is `url` and the value is the `selfLinks` of the related entities.

#### Example 16: an example of addressing to an association link

**Example Request:** `http://example.org/v1.0/Datastreams(1)/Observations/$ref` returns all the
`selfLinks` of the `Observations` of `Datastream(1)`.

**Example Response:**

```json
{
  "value": [
    {
      "@iot.selfLinks": "http://example.org/v1.0/Observations(1)"
    },
    {
      "@iot.selfLinks": "http://example.org/v1.0/Observations(2)"
    }
  ]
}
```

#### 9.2.8 Usage 8: nested resource path

As users can use navigation properties to link from one entity set to another, users can further extend the resource path with unique identifiers, properties, or links (*i.e.*, Usage 3, 4 and 6).

#### Example 17: examples of nested resource path

**Example Request 1:** `http://example.org/v1.0/Datastreams(1)/Observations(1)` returns a specific
`Observation` entity in the `Datastream`.

**Example Request 2:** `http://example.org/v1.0/Datastreams(1)/Observations(1)/resultTime`
turns the resultTime property of the specified `Observation` in the `Datastream`.

**Example Request 3:** `http://example.org/v1.0/Datastreams(1)/Observations(1)/FeatureOfInterest` returns the `FeatureOfInterest` entity of the specified `Observation` in the `Datastream`.

### 9.3 Requesting Data

Clients issue HTTP `GET` requests to OGC SensorThings API services for data.

The resource path of the URL specifies the target of the request. Additional query operators can be specified
through query options that are presented as follows.

    Req 17    OGC SensorThings API services are hypermedia driven services that return URLs to the client. If a client subsequently requests the advertised resource and the URL has expired, then the service SHOULD respond with 410 Gone. If this is not feasible, the service SHALL respond with 404 Not Found.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/status-code

#### 9.3.1 Evaluating System Query Options

    Req 18    An OGC SensorThings API service SHALL evaluate the system query options following the order specified in Section 9.3.1.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/order

The OGC SensorThings API adapts many of OData’s system query options and their usage. These query options allow refining the request.

The result of the service request is as if the system query options were evaluated in the following order.

Prior to applying any server-driven pagination:

* `$filter`
* `$count`
* `$orderby`
* `$skip`
* `$top`

After applying any server-driven pagination:

* `$expand`
* `$select`

#### 9.3.2 Specifying Properties to Return

The `$select` and `$expand` system query options enable the client to specify the set of properties to be included in a response.

##### 9.3.2.1 `$expand`

    Req 19    The usage of the $select query option SHALL be as defined in Section 9.3.2.1.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/expand

The `$expand` system query option indicates the related entities to be represented inline. The value of the `$expand` query option must be a comma separated list of navigation property names. Additionally each navigation property can be followed by a forward slash and another navigation property to enable identifying a multi-level relationship.

#### Example 18: examples of `$expand` query option

**Example 1:** `http://example.org/v1.0/Things?$expand=Datastreams` returns the entity set of `Things` as well as each of the `Datastreams` associated with each `Thing` entity.

**Example 2:** `http://example.org/v1.0/Things?$expand=Datastreams/ObservedProperty` returns the collection of `Things`, the `Datastreams` associated with each `Thing`, and the `ObservedProperty` associated with each `Datastream`.

**Example 3:** `http://example.org/v1.0/Datastreams(1)?$expand=Observations,ObservedProperty` returns the `Datastream` whose `id` is 1 as well as the `Observations` and `ObservedProperty` associated with this `Datastream`.

Query options can be applied to the expanded navigation property by appending a semicolon-separated list of query options, enclosed in parentheses, to the navigation property name. Allowed system query options are `$filter`, `$select`, `$orderby`, `$skip`, `$top`, `$count`, and `$expand`.

[Adapted from OData 4.0- URL 5.1.2]

**Example 4:** `http://example.org/v1.0/Datastreams(1)?$expand=Observations($filter=result eq 1)` returns the `Datastream` whose `id` is 1 as well as its `Observations` with a `result` equal to 1.

##### 9.3.2.2 `$select`

    Req 20    The usage of the $select query option SHALL be as defined in Section 9.3.2.2.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/select

The `$select` system query option requests that the service to return only the properties explicitly requested by the client. The value of a `$select` query option is a comma-separated list of selection clauses. Each selection clause may be a property name (including navigation property names). The service returns the specified content, if available, along with any available expanded navigation properties.

[Adapted from OData 4.0-Protocol 11.2.4.1]

#### Example 19: examples of `$select` query option

**Example 1:** `http://example.org/v1.0/Observations?$select=result,resultTime` returns only the
`result` and `resultTime` properties for each `Observation` entity.

**Example 2:** `http://example.org/v1.0/Datasteams(1)?$select=id,Observations&$expand=Observations/FeatureOfInterest` returns the `id` property of the `Datastream` entity, and all the properties of the entity identified by the `Observations` and `FeatureOfInterest` navigation properties.

**Example 3:** `http://example.org/v1.0/Datastreams(1)?$expand=Observations($select=result)` returns the `Datastream` whose `id` is 1 as well as the `result` property of the entity identified by the `Observations` navigation property.

### 9.4 Query Entity Sets

The OGC SensorThings API services support requests for data via `HTTP GET` requests. Clients can apply query operators to further process the addressed resources. The query operators are prefixed with a dollar (`$`) character and specified as key-value pairs after the question symbol "`?`" in the request URI. Many of the OGC SensorThings API’s query options are adapted from OData’s query options. OData developers should be able to pick up SensorThings API query options very quickly.

    Req 21    If a service does not support a system query option, it SHALL fail any request that contains the unsupported option and SHOULD return 501 Not Implemented.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/query-status-code

#### 9.4.1 `$orderby`

    Req 22    The usage of the $orderby query option SHALL be as defined in Section 9.4.1.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/orderBy

The `$orderby` system query option specifies the order in which items are returned from the service.

The value of the `$orderby` system query option contains a comma-separated list of expressions whose primitive result values are used to sort the items. A special case of such an expression is a property path terminating on a primitive property. A type cast using the qualified entity type name is required to order by a property defined on a derived type.

The expression can include the suffix `asc` for ascending or `desc` for descending, separated from the property name by one or more spaces. If `asc` or `desc` is not specified, the service orders by the specified property in ascending order.

Null values come before non-null values when sorting in ascending order and after non-null values when sorting in descending order.

Items are sorted by the result values of the first expression, and then items with the same value for the first expression are sorted by the result value of the second expression, and so on.

[Note: Adapted from OData 4.0-Protocol 11.2.5.2]

#### Example 20: examples of `$orderby` query option

**Example 1:** `http://example.org/v1.0/Observations?$orderby=result` returns all `Observations`
ordered by the `result` property in ascending order.

Example 2: `http://example.org/v1.0/Observations?$expand=Datastream&$orderby=Datastreams/id desc, phenomenonTime` returns all `Observations` ordered by the `id` property of the linked `Datastream` entry in descending order, then by the `phenomenonTime` property of `Observations` in ascending order.

#### 9.4.2 `$top`

    Req 23    The usage of the $top query option SHALL be as defined in Section 9.4.2.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/top

The `$top` system query option specifies a non-negative integer n that limits the number of items returned from a collection of entities. The service returns the number of available items up to but not greater than the specified value n.

If no unique ordering is imposed through an `$orderby` query option, the service imposes a stable ordering across requests that include `$top`.

[Note: Adapted from OData 4.0-Protocol 11.2.5.3]

In addition, if the `$top` value exceeds the service-driven pagination limitation (*i.e.*, the largest number of entities the service can return in a single response), the `$top` query option is discarded and the server-side pagination limitation is imposed.

#### Example 21: examples of `$top` query option

**Example 1:** `http://example.org/v1.0/Things?$top=5` returns only the first five entities in the `Things`
collection.

**Example 2:** `http://example.org/v1.0/Observations?$top=5&$orderby=phenomenonTime desc` returns the first five `Observation` entries after sorted by the `phenomenonTime` property in descending order.

#### 9.4.3 `$skip`

    Req 24    The usage of the $skip query option SHALL be as defined in Section 9.4.3.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/skip

The `$skip` system query option specifies a non-negative integer n that excludes the first n items of the queried collection from the result. The service returns items starting at position n+1.

#### Example 22: examples of `$skip` query option

**Example 1:** `http://example.org/v1.0/Things?$skip=5` returns `Thing` entities starting with the sixth
`Thing` entity in the `Things` collection.

Where `$top` and `$skip` are used together, `$skip` is applied before `$top`, regardless of the order in which they appear in the request.

If no unique ordering is imposed through an `$orderby` query option, the service imposes a stable ordering
across requests that include `$skip`.

[Note: Adapted from OData 4.0-Protocol 11.2.5.4]

**Example 2:** `http://example.org/v1.0/Observations?$skip=2&$top=2&$orderby=resultTime` returns the third and fourth `Observation` entities from the collection of all `Observation` entities when the collection is sorted by the `resultTime` property in ascending order.

#### 9.4.4 `$count`

    Req 25    The usage of the $count query option SHALL be as defined in Section 9.4.4.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/count

The `$count` system query option with a value of true specifies that the total count of items within a collection matching the request be returned along with the result.

A `$count` query option with a value of `false` (or not specified) hints that the service does not return a count.

The service returns an HTTP Status code of `400 Bad Request` if a value other than `true` or `false` is
specified.

The `$count` system query option ignores any `$top`, `$skip`, or `$expand` query options, and returns the total count of results across all pages including only those results matching any specified `$filter`. Clients should be aware that the count returned inline may not exactly equal the actual number of items returned, due to latency between calculating the count and enumerating the last value or due to inexact calculations on the service.

[Adapted from OData 4.0-Protocol 11.2.5.5]

#### Example 23: examples of `$count` query option

**Example 1:** `http://example.org/v1.0/Things?$count=true` return, along with the results, the total
number of `Things` in the collection.

**Example Response:**

```json
{
  "@iot.count": 2,
  "value": [
    // Entities omitted for example
  ]
}
```

#### 9.4.5 `$filter`

    Req 26    The usage of the $filter query option SHALL be as defined in Section 9.4.5
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/filter

The `$filter` system query option allows clients to filter a collection of entities that are addressed by a request URL. The expression specified with `$filter` is evaluated for each entity in the collection, and only items where the expression evaluates to true are included in the response. Entities for which the expression evaluates to false or to null, or which reference properties that are unavailable due to permissions, are omitted from the response.

[Adapted from Data 4.0-URL Conventions 5.1.1]

The expression language that is used in `$filter` operators supports references to properties and literals. The literal values can be strings enclosed in single quotes, numbers and boolean values (true or false) or datetime values represented as ISO 8601 time string.

#### Example 24: examples of `$filter` query option

**Example 1:** `http://example.org/v1.0/Observations?$filter=result lt 10.00` returns all
`Observations` whose `result` is less than 10.00.

In addition, clients can choose to use the properties of linked entities in the `$filter` predicate. The following are examples of the possible uses of the `$filter` in the data model of the SensorThings service.

**Example 2:** `http://example.org/v1.0/Observations?$filter=Datastream/id eq '1'` returns all
`Observations` whose `Datastream’s` `id` is 1.

**Example 3:** `http://example.org/v1.0/Things?$filter=geo.distance(Locations/location,geography'POINT(-122, 43)') gt 1` returns `Things` that the distance between their last known locations and `POINT(-122 43)` is greater than 1.

**Example 4:** ` http://example.org/v1.0/Things?$expand=Datastreams/Observations/FeatureOfInterest&$filter=Datastreams/Observations/FeatureOfInterest/id eq 'FOI_1' and Datastreams/Observations/resultTime ge 2010-06-01T00:00:00Z and Datastreams/Observations/resultTime le 2010-07-01T00:00:00Z` returns `Things` that have any observations of a feature of interest with a unique identifier equals to '`FOI_1`' in June 2010.

##### 9.4.5.1 Built-in filter operations

The OGC SensorThings API supports a set of built-in filter operations, as described in the following table. These built-in filter operator usages and definitions follow the [OData Specification Section 11.2.5.1.1] and [OData Version 4.0 ABNF].

    Req 27    The built-in filter operators SHALL be as defined in Table 9-1.
    http://www.opengis.net/spec/iot_sensing/1.0/req/request-data/built-in-filter-operations

#### Table 9-1 Built-in Filter Operators

<table>
  <thead>
    <tr>
      <th>Operator</th>
      <th>Description</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th colspan="3">Comparison Operators</th>
    </tr>
    <tr>
      <td><code>eq</code></td>
      <td>Equal</td>
      <td><code>/ObservedProperties?$filter=unitOfMeasurement/name eq 'degree Celsius'</code></td>
    </tr>
    <tr>
      <td><code>ne</code></td>
      <td>Not equal</td>
      <td><code>/ObservedProperties?$filter=unitOfMeasurement/name ne 'degree Celsius'</code></td>
    </tr>
    <tr>
      <td><code>gt</code></td>
      <td>Greater than</td>
      <td><code>/Observations?$filter=result gt 20.0</code></td>
    </tr>
    <tr>
      <td><code>ge</code></td>
      <td>Greater than or equal</td>
      <td><code>/Observations?$filter=result ge 20.0</code></td>
    </tr>
    <tr>
      <td><code>lt</code></td>
      <td>Less than</td>
      <td><code>/Observations?$filter=result lt 100</code></td>
    </tr>
    <tr>
      <td><code>le</code></td>
      <td>Less than or equal</td>
      <td><code>/Observations?$filter=result le 100</code></td>
    </tr>
    <tr>
      <th colspan="3">Logical Operators</th>
    </tr>
    <tr>
      <td><code>and</code></td>
      <td>Logical and</td>
      <td><code>/Observations?$filter=result le 3.5 and FeatureOfInterest/id eq '1'</code></td>
    </tr>
    <tr>
      <td><code>or</code></td>
      <td>Logical or</td>
      <td><code>/Observations?$filter=result gt 20 or result le 3.5</code></td>
    </tr>
    <tr>
      <td><code>not</code></td>
      <td>Logical negation</td>
      <td><code>/Things?$filter=not startswith(description,'test')</code></td>
    </tr>
    <tr>
      <th colspan="3">Arithmetic Operators</th>
    </tr>
    <tr>
      <td><code>add</code></td>
      <td>Addition</td>
      <td><code>/Observations?$filter=result add 5 gt 10</code></td>
    </tr>
    <tr>
      <td><code>sub</code></td>
      <td>Subtraction</td>
      <td><code>/Observations?$filter=result sub 5 gt 10</code></td>
    </tr>
    <tr>
      <td><code>mul</code></td>
      <td>Multiplication</td>
      <td><code>/Observations?$filter=result mul 2 gt 2000</code></td>
    </tr>
    <tr>
      <td><code>div</code></td>
      <td>Division</td>
      <td><code>/Observations?$filter=result div 2 gt 4</code></td>
    </tr>
    <tr>
      <td><code>mod</code></td>
      <td>Modulo</td>
      <td><code>/Observations?$filter=result mod 2 eq 0</code></td>
    </tr>
    <tr>
      <th colspan="3">Grouping Operators</th>
    </tr>
    <tr>
      <td><code>( )</code></td>
      <td>Precedence grouping</td>
      <td><code>/Observations?$filter=(result sub 5) gt 10</code></td>
    </tr>
  </tbody>
</table>

