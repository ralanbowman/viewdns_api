## Find the ping response time from a remote system 

Find the response time using `ping` from a remote server to the ViewDNS server in order to troubleshoot or test network latency. 

### Method and URL

`GET http://pro.viewdns.info/ping/`

### Sample Request and Query Parameters

`curl -X GET http://pro.viewdns.info/ping/?host=example.com&apikey=yourapikey&output=output_type`

| Element | Description | Type | Required | Notes |
|---------|-------------|------|----------|-------|
| **host** | Domain name or IP address to ping | URL parameter | Required | IPv4 support only | 
| **apikey** | Your ViewDNS API key | URL parameter | Required | | 
| **output** | The output format of the response | URL parameter | Required | **json** or **xml** |


### Sample Response

**JSON response (output=json)**

```json
{
    "query": {
        "tool": "ping_PRO",
        "host": "example.com"
    },
    "response": {
        "replys": [
            {
                "rtt": "32.5 ms"
            },
            {
                "rtt": "36.2 ms"
            },
            {
                "rtt": "30.8 ms"
            },
            {
                "rtt": "36.6 ms"
            }
        ]
    }
}
```
<br />

**XML response (output=xml)**

```xml
<?xml version='1.0' encoding='ISO-8859-1'?>
<viewdns>
  <query>
    <tool>ping_PRO</tool>
    <host>example.com</host>
  </query>
  <response>
    <rtt>32.5 ms</rtt>
    <rtt>36.2 ms</rtt>
    <rtt>30.8 ms</rtt>
    <rtt>36.6 ms</rtt>
  </response>
</viewdns>
```

| Element     |   Description   |   Type   |   Notes   |
|-------------|-----------------|----------|-----------|
| **viewdns** | Top level XML only | viewdns data object | |
| **query** | Query response | JSON object (json) / query data object (xml) | |
| query/**tool** | Name of lookup tool | string | Tool name is **ping_PRO** | 
| query/**host** | Domain or IP address queried | string | |
| **response** | Ping query response | JSON object (json) / response data object (xml) | **NOTE** - if there is no ping response the reply will be empty |
| response/**replys** | Ping replies | JSON array | Not available in XML response |
| response/**rtt** | Ping response time | string | The time for the ping response to return  to the ViewDNS servers |
