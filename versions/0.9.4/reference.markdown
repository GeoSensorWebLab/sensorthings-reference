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
