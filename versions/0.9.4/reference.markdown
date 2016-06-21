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
