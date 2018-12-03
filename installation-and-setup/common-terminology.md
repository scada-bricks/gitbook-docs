---
description: >-
  This page outlines the concept of the terminology used across SCADA bricks.
  Although this terminology is not mandatory, many services follow it for
  consistency across the framework.
---

# Common terminology

### Service / Module / Brick

The above words are all used interchangeably to describe a single piece of the framework.  Each service generally has one specific function only.

### Dataset

Dataset is a generic term used to partition and namespace data.  It is assumed that all tag and device names are unique within a dataset.  A dataset usually relates to a type of data at specific site, and the name would usually include the site name plus the data type name, e.g. **london-array-wind-farm-siemens-scada**.   However, sometimes due to the nature of the source data, datasets can be more granular, and cover different parts of the system etc.  Additionally, translator/consolidator services may combine / split datasets for consumption further upstream.

### Device

A device is usually related to a physical device on the site that has time series data recorded against it. Device names are unique and usually share the same list of tags within a dataset.

### Tag

A tag is a name given to a particular measurement, such as temperatures, power readings or wind speeds.  Although in traditional SCADA tags usually relate more to realtime readings, SCADA bricks extends this to cover field names in historic databases too.







