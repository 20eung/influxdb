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
| version
