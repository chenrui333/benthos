---
title: amqp_1
type: output
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/output/amqp_1.go
-->


BETA: This output is currently in a BETA stage and is therefore subject to
breaking configuration changes outside of major version releases.

Sends messages to an AMQP (1.0) server.


import Tabs from '@theme/Tabs';

<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

import TabItem from '@theme/TabItem';

<TabItem value="common">

```yaml
# Common config fields, showing default values
output:
  amqp_1:
    url: ""
    target_address: ""
    max_in_flight: 1
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
output:
  amqp_1:
    url: ""
    target_address: ""
    max_in_flight: 1
    tls:
      enabled: false
      skip_cert_verify: false
      root_cas_file: ""
      client_certs: []
```

</TabItem>
</Tabs>


## Performance

This output benefits from sending multiple messages in flight in parallel for
improved performance. You can tune the max number of in flight messages with the
field `max_in_flight`.

## Fields

### `url`

A URL to connect to.


Type: `string`  
Default: `""`  

```yaml
# Examples

url: amqp://localhost:5672/

url: amqps://guest:guest@localhost:5672/
```

### `target_address`

The target address to write to.


Type: `string`  
Default: `""`  

```yaml
# Examples

target_address: /foo

target_address: queue:/bar

target_address: topic:/baz
```

### `max_in_flight`

The maximum number of messages to have in flight at a given time. Increase this to improve throughput.


Type: `number`  
Default: `1`  

### `tls`

Custom TLS settings can be used to override system defaults.


Type: `object`  
Default: `{"client_certs":[],"enabled":false,"root_cas_file":"","skip_cert_verify":false}`  

### `tls.enabled`

Whether custom TLS settings are enabled.


Type: `bool`  
Default: `false`  

### `tls.skip_cert_verify`

Whether to skip server side certificate verification.


Type: `bool`  
Default: `false`  

### `tls.root_cas_file`

The path of a root certificate authority file to use.


Type: `string`  
Default: `""`  

### `tls.client_certs`

A list of client certificates to use.


Type: `array`  
Default: `[]`  

```yaml
# Examples

client_certs:
  - cert: foo
    key: bar

client_certs:
  - cert_file: ./example.pem
    key_file: ./example.key
```

