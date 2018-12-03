---
description: This page suggests some steps to get started with some of the core modules.
---

# Getting started

We are still in the early phases of specifying how this platform will work, and getting the core modules developed.

Check back here soon, and we should have some details of how to get started. 

If you wish to be involved or find out more about this project, contact paul.grimshaw@sennen.tech in the first instance.

## Example

Below an example scada bricks setup is outlined, detailing the module and the relevant contracts implemented by the module.

The example is a basic example that fetches real-time data from a Siemens OPC XML DA, translating the tags to the IEC 61400-25 format and storing in a postgres database.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Module Name</th>
      <th style="text-align:left">Contracts implemented</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Siemens wind turbines</td>
      <td style="text-align:left">None</td>
      <td style="text-align:left">This is the standard OPC XML DA interface that is available on most Siemens
        wind turbine sites. In this example setup, this is the base data source
        that is read in. This is not a SCADA bricks module, but is noted here to
        assist in understanding the setup.</td>
    </tr>
    <tr>
      <td style="text-align:left">OPC XML DA</td>
      <td style="text-align:left">
        <p><b>real-time-scada</b>
        </p>
        <p><b></b>
        </p>
        <p><b>configurable-service</b>
        </p>
      </td>
      <td style="text-align:left">The lowest level brick in this example is a real-time-scada interface,
        which can be configured to communicate with multiple OPC XML DA interfaces.
        This is configured via a centralised config service to communicate with
        1 or more wind turbine OPC XML DA endpoints. In practice, this may be close
        to the datasource on a remote server (more commonly), or in the cloud.</td>
    </tr>
    <tr>
      <td style="text-align:left">Standard tag translator</td>
      <td style="text-align:left">
        <p><b>real-time-scada</b>
        </p>
        <p><b></b>
        </p>
        <p><b>configurable service</b>
        </p>
      </td>
      <td style="text-align:left">This is a simple module that translates tags. Given a set of config, it
        translates real-time tags reads and writes from one or more other real-time-scada
        modules, and renames them. In this example setup, this interface has been
        configured to translate the OEM specific wind turbine SCADA names to standard
        names defined in the IEC 61400-25 specification. Other services can read
        tags from this service rather than the source services to enable communication
        in a standard way. Other forms of tag "translators" or "consolidators"
        are possible, but this one (Simple tag translator) simply maps tags one-to-one
        from the source name to a target name.</td>
    </tr>
    <tr>
      <td style="text-align:left">Postgres DW historian</td>
      <td style="text-align:left">
        <p><b>real-time-historian,</b>
        </p>
        <p><b></b>
        </p>
        <p><b>historic-data-source</b>
        </p>
        <p><b></b>
        </p>
        <p><b>configurable-service</b>
        </p>
        <p><b></b>
        </p>
        <p><b>schedule-enabled-service</b>
        </p>
      </td>
      <td style="text-align:left">This module fetches data from one or more real-time-scada modules and
        stores the results in a historic data source (in this case a postgres data
        warehouse). The frequency and scheduling is driven by an external scheduler
        service, hence this module also implements the schedule-enabled-service.
        In this case, the module also implements the historic-data-source contract,
        which means other services may talk to it and fetch data according to that
        contract. The service config would include the tags to fetch and store
        from the above tag translator service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Mongo scheduler</td>
      <td style="text-align:left">
        <p><b>configurable-service</b>
        </p>
        <p></p>
        <p><b>scheduler</b>
        </p>
      </td>
      <td style="text-align:left">A scheduler service is responsible for scheduling other services, and
        in this example it is set to schedule the above historian service to run
        at 1hz (once per second). As a result, this service would call the "run"
        method on the historian service every second, the target service storing
        the fetched data into postgres.</td>
    </tr>
  </tbody>
</table>

