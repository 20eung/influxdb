# InfluxDB Query Example

## 1. Measurement 목록 확인

저장된 모든 Measurement(테이블과 유사)의 이름을 확인합니다.

```sql
SHOW MEASUREMENTS
```

| name |
|---|
| bgp_src_as_count | 
| netflow | 
| netflow_options | 



## 2. Measurement의 필드(Key/Value) 확인

특정 Measurement에서 사용 가능한 필드를 확인합니다.

```sql
SHOW FIELD KEYS FROM <measurement_name>
```

예: ```netflow``` Measurement에서 필드 확인

```sql
SHOW FIELD KEYS FROM netflow
```

| fieldKey | fieldType
|---|---|
| in_bytes | integer |
| in_packets | integer |
| in_snmp | integer | 
| ip_version | string |
| last_switched | integer |
| max_packet_len | integer |
| max_ttl | integer |
| min_packet_len | integer |
| min_ttl | integer | 
| next_hop | string | 
| out_snmp | integer | 
| protocol | string | 
| replication_factor | integer | 
| src | string | 
| src_mask | integer | 
| src_port | integer | 
| src_tos | string | 
| tcp_flags | string | 

## 3. Measurement의 태그(Tag Key) 확인

태그는 데이터를 그룹화하거나 필터링하는 데 사용됩니다.

```sql
SHOW TAG KEYS FROM <measurement_name>
```

예: ```netflow``` Measurement에서 태그 확인

```sql
SHOW TAG KEYS FROM netflow
```

| tagKey |
| --- |
| dst |
| host |
| source |
| src |
| version |


## 4. Retention Policy 확인

Retention Policy는 데이터의 보존 기간과 관련됩니다.

```sql
SHOW RETENTION POLICIES ON <database_name>
```

예: ```netflow``` 데이터베이스에서 Retention Policy 확인

```sql
SHOW RETENTION POLICIES ON netflow
```

| name | duration | shardGroupDuration | replicaN | default |
| --- | --- | --- | --- | --- |  
| autogen | 0s | 168h0m0s | 1 | true | 


## 5. 샘플 데이터 확인

특정 Measurement의 데이터를 일부 확인하여 구조를 파악합니다.

```sql
SELECT * FROM <measurement_name> LIMIT 5
```

예: ```netflow``` Measurement에서 데이터 샘플 확인

```sql
SELECT * FROM netflow LIMIT 5
```

| Time | bgp_dst_as | bgp_next_hop | bgp_src_as | direction | dst | dst_mask | dst_port | first_switched | fwd_reason | fwd_status | host | icmp_code | icmp_type | in_bytes | in_packets | in_snmp | ip_version | last_switched | max_packet_len | max_ttl | min_packet_len | min_ttl | next_hop | out_snmp | protocol | replication_factor | source | src | src_mask | src_port | src_tos | tcp_flags | version | 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| 2024-12-06 19:19:58.099 | 10049 | 210.211.95.90 | 4766 | egress | 211.45.37.231 | 25 | 443 | 4226714262 | not fragmented | forwarded | grafana | 0 | 0 | 93 | 1 | 0 | IPv4 | 4226714262 | 93 | 117 | 93 | 117 | 0.0.0.0 | 259 | tcp | 0 | 210.211.95.237 | 222.117.111.2 | 13 | 60417 | 0x00 | ...AP... | NetFlowV9 | 
| 2024-12-06 19:19:58.099 | 10049 | 210.211.95.38 | 9318 | ingress | 124.66.185.32 | 24 | 514 | 4226714312 | unknown | forwarded | grafana | 0 | 0 | 311 | 1 | 257 | IPv4 | 4226714312 | 311 | 58 | 311 | 58 | 210.211.95.38 | 264 | udp | 0 | 210.211.95.237 | 218.49.70.130 | 15 | 50604 | 0x00 | ........ | NetFlowV9 | 
| 2024-12-06 19:19:58.099 | 10049 | 210.211.95.90 | 9318 | ingress | 211.45.51.130 | 28 | 443 | 4226714272 | unknown | forwarded | grafana | 0 | 0 | 252 | 1 | 257 | IPv4 | 4226714272 | 252 | 122 | 252 | 122 | 210.211.95.94 | 262 | tcp | 0 | 210.211.95.237 | 1.227.133.88 | 13 | 5957 | 0x00 | ...AP... | NetFlowV9 | 
| 2024-12-06 19:19:58.099 | 10049 | 210.211.95.38 | 9318 | egress | 211.45.59.22 | 24 | 0 | 4226714322 | not fragmented | forwarded | grafana | 0 | 0 | 96 | 1 | 0 | IPv4 | 4226714322 | 96 | 57 | 96 | 57 | 0.0.0.0 | 259 | esp | 0 | 210.211.95.237 | 180.71.247.147 | 16 | 0 | 0x00 | ........ | NetFlowV9 | 
| 2024-12-06 19:19:58.099 | 10049 | 210.211.95.38 | 9318 | egress | 211.45.59.22 | 24 | 0 | 4226714242 | not fragmented | forwarded | grafana | 0 | 0 | 96 | 1 | 0 | IPv4 | 4226714242 | 96 | 57 | 96 | 57 | 0.0.0.0 | 264 | esp | 0 | 210.211.95.237 | 222.237.84.202 | 13 | 0 | 0x00 | ........ | NetFlowV9 | 
