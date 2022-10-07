---
title: v1.fieldKeys() function
description: >
  `v1.fieldKeys()` returns field keys in a bucket.
menu:
  flux_0_x_ref:
    name: v1.fieldKeys
    parent: influxdata/influxdb/v1
    identifier: influxdata/influxdb/v1/fieldKeys
weight: 301
flux/v0.x/tags: [metadata]
deprecated: 0.88.0
---

<!------------------------------------------------------------------------------

IMPORTANT: This page was generated from comments in the Flux source code. Any
edits made directly to this page will be overwritten the next time the
documentation is generated. 

To make updates to this documentation, update the function comments above the
function definition in the Flux source code:

https://github.com/influxdata/flux/blob/master/stdlib/influxdata/influxdb/v1/v1.flux#L337-L337

Contributing to Flux: https://github.com/influxdata/flux#contributing
Fluxdoc syntax: https://github.com/influxdata/flux/blob/master/docs/fluxdoc.md

------------------------------------------------------------------------------->

`v1.fieldKeys()` returns field keys in a bucket.

Results include a single table with a single column, `_value`.

**Note**: FieldKeys is a special application of `tagValues that returns field
keys in a given bucket.

##### Function type signature

```js
(
    bucket: string,
    ?predicate: (
        r: {
            A with
            _value: B,
            _time: time,
            _stop: time,
            _start: time,
            _measurement: string,
            _field: string,
        },
    ) => bool,
    ?start: C,
    ?stop: D,
) => stream[E] where E: Record
```

{{% caption %}}For more information, see [Function type signatures](/flux/v0.x/function-type-signatures/).{{% /caption %}}

## Parameters

### bucket
({{< req >}})
Bucket to list field keys from.



### predicate

Predicate function that filters field keys.
Default is `(r) => true`.



### start

Oldest time to include in results. Default is `-30d`.



### stop

Newest time include in results.
The stop time is exclusive, meaning values with a time equal to stop time are excluded from the results.
Default is `now()`.

Relative start times are defined using negative durations.
Negative durations are relative to `now()`.
Absolute start times are defined using time values.


## Examples

### Query field keys from an InfluxDB bucket

```js
import "influxdata/influxdb/schema"

schema.fieldKeys(bucket: "example-bucket")

```
