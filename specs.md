---
layout: page
title: "Specifications"
permalink: /specs/
---


## Data Fields
All resulting data is stored in tab-separated-value ``TSV`` files easily openable with spreadsheet or text-editor software. This format is also supported by most software applications as well. When data is too large to store in a single file, multiple partition data files will be available. Each of these files consists of the following columns.


### Identification
These fields are always available & are used to identify a space-time slice.

| Field | Type | Description |
| ----- | ---- | ----------- |
| area\_id | UUID | Unique hexadecimal string identifying specific areas. This field is part of the space-time key & is useful to join with other {{site.copyright.name}} data products. |
| time\_start | timestamp | Inclusive UTC moment in time when measurement begins. In the form of ``YYYY-MM-DD hh:mm:ss+00`` |
| time\_finish | timestamp | Exclusive UTC moment in time when measurement ends. In the form of ``YYYY-MM-DD hh:mm:ss+00`` |
{: .table .table-striped .table-hover}


### Normalization
These fields provide auxiliary contextual information to normalize payload as necessary.

| Field | Type | Description |
| ----- | ---- | ----------- |
| time\_zone | list | ISO timezone code identifying the measured area’s time offset from UTC. This is useful to make relative time comparisons between regions that have different time zones. For large un-granular areas that span multiple time zones, all applicable codes are listed by decreasing surface area coverage. |
| population | real | Interpolated number of people living in the measured area. These are derived from 2016 Census Canada but enhanced for habitable hyper-local areas. This is useful for transforming scores to absolute per capita values when comparing across different areas & time periods. |
| area\_km2 | real | Total projected surface in km2 of the measured area including waters & land regions. This is useful for transforming scores to absolute per area values when comparing across different areas & time periods. |
{: .table .table-striped .table-hover}


### Visualization
These optional fields are provied to visualize results on a map.

| Field | Type | Description |
| ----- | ---- | ----------- |
| geom | WKT, GeoJSON or lat/lng | Geometry describing the measured area. These are encoded in standard format usable in other geo-spatial tools. Geometries are useful for visualisation or analytical purposes. They may be expressed as exact polygon areas or simplified as centroid points. |
{: .table .table-striped .table-hover}


### Sentiment Payload
These fields correspond to the sentiment data product being measured.

| Field | Type | Description |
| ----- | ---- | ----------- |
| sentiment.neg | percent | Relative proportion of negative sentiment measured in the given space-time. |
| sentiment.neu | percent | Relative proportion of neutral sentiment measured in the given space-time. |
| sentiment.pos | percent | Relative proportion of positive sentiment measured in the given space-time. |
{: .table .table-striped .table-hover}


### Quality Tracking
These fields provide a quality indication of each measurement.

| Field | Type | Description |
| ----- | ---- | ----------- |
| audit.n | integer | Number of total events within the space-time used to derive the sentiment. This is useful to gauge activity volume & statistical validity of measurement. |
| audit.conf | percent | Average confidence of all sentiments within the measured space-time. This is useful to gauge the strength of the result. |
{: .table .table-striped .table-hover}
