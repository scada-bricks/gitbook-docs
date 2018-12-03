---
description: >-
  This project is an open source, language and platform agnostic SCADA toolset. 
  It has been developed for the renewables industry, to collect, store and
  analyse time series data.
---

# SCADA Bricks - the open SCADA project

## What is SCADA Bricks?

SCADA Bricks is an entirely modular, open source framework, with modules focused on time series data acquisition, storage and analysis from a variety of devices.  

The following are some of the core functions:

* Standard adapters to multiple real-time and historic interfaces \(OPC / ODBC\)
* Mapping and translation to standard formats \(IEC etc\)
* Local store-and-forward ****for remote systems
* Standardised cloud storage
* Industry specific data analysis modules and dashboards

There is no "central service" or code base of any kind, everything is made up of individual modules.  Everything is replaceable and optional.  However, we live by the philosophy **batteries included buy replaceable** \(credit to Docker\).  Getting started should be quick and easy.

## Technology

SCADA Bricks is entirely language and platform agnostic.  It is based on a very simple set of definitions \(**contracts**\), which define **HTTP** interfaces that services should implement.

Every service should ideally be setup in **docker** and published to a docker repository. This way, services can be setup and installed quickly and easily by anyone.

Linux based containers are preferred, but windows images are also supported

## License and pricing

Everything in the core project is licensed under an MIT license \(basically do with it what you want\).  Other parties are welcome to offer paid modules, or fees for consultancy for setup of SCADA bricks.

