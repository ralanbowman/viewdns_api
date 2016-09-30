# ViewDNS API 

An API to query the tools available at [ViewDNS](http://viewdns.info). Requests and responses are available in JSON and XML. 

**NOTE** - you need to register for an API key in order to use this API. More information is available on the [API plans](http://viewdns.info/api/) page. 

This is only a small selection of the tools available from ViewDNS. 

[Find the IP address location](#find-the-ip-address-location)  
[Find the Abuse contact info for a domain](#find-the-abuse-contact-info-for-a-domain)  
[Find the ping response time from a remote system](#find-the-ping-response-time-from-a-remote-system)  

[Status Codes and Errors](#status-codes-and-errors)  


## Find the IP address location

Find the city, country, latitude and longitude, and other information about an IP address.

### Method and URL

`GET http://pro.viewdns.info/iplocation/`

### Sample Request and Query Parameters

`curl -X GET http://pro.viewdns.info/iplocation/?ip=12.34.56.78&apikey=yourapikey&output=output_type`

| Element | Description | Type | Required | Notes |
|---------|-------------|------|----------|-------|
| **ip** | The IP address to find the location for | URL parameter | Required | IPv4 support only | 
| **apikey** | Your ViewDNS API key | URL parameter | Required | | 
| **output** | The output format of the response | URL parameter | Required | **json** or **xml** |


### Sample Response

**NOTE** - the exact responses returned (city, zipcode, region_code, etc) will vary depending on the information available for an IP address.

**JSON response (output=json)**

```json
{
    "query": {
        "tool": "iplocation_PRO",
        "ip": "12.34.56.78"
    },
    "response": {
        "city": "Anytown",
        "zipcode": "12345",
        "region_code": "AA",
        "region_name": "State",
        "country_code": "US",
        "country_name": "United States",
        "latitude": "39.9968",
        "longitude": "-82.9882",
        "gmt_offset": "",
        "dst_offset": ""
    }
}
```
<br />

**XML response (output=xml)**

```xml
<?xml version='1.0' encoding='ISO-8859-1'?>
<viewdns>
  <query>
    <tool>iplocation_PRO</tool>
    <ip>12.34.56.78</ip>
  </query>
  <response>
    <city>Anytown</city>
    <zipcode>12345</zipcode>
    <region_code>AA</region_code>
    <region_name>State</region_name>
    <country_code>US</country_code>
    <country_name>United States</country_name>
    <latitude>39.9968</latitude>
    <longitude>-82.9882</longitude>
    <gmt_offset></gmt_offset>
    <dst_offset></dst_offset>
  </response>
</viewdns>
```


| Element | Description | Type | Notes |
|---------|-------------|------|-------|
| **viewdns** | Top level XML only | viewdns data object | |
| **query** | Top level | JSON object (json) / query data object (xml) | |
| query/**tool** | Name of lookup tool | string | Tool name is **iplocation_PRO** | 
| query/**ip** | IP address queried | string | |
| **response** | IP query response | JSON object (json) / query data object (xml) |  |
| response/**city** | City location | string |  | 
| response/**zipcode** | Zip code location | string | Zip code or Postal code | 
| response/**region_code** | Two letter region or state code | string | | 
| response/**region_name** | Common name for region | string | | 
| response/**country_code** | Two letter country code | string | |
| response/**country_name** | Common name for country | string | | 
| response/**latitude** | Latitude of IP location | string | |
| response/**longitude** | Longitude of IP location | string | |
| response/**gmt_offset** | Offset from GMT | string | |
| response/**dst_offset** | Offset for DST | string | |

<br />


## Find the Abuse contact info for a domain 

Look up the Abuse contact info for a domain in order to send complaints/warnings about spam or other malicious behavior. 

### Method and URL

`GET http://pro.viewdns.info/abuselookup`

### Sample Request and Query Parameters

`curl -X GET "http://pro.viewdns.info/abuselookup/?domain=example.com&apikey=yourapikey&output=output_type"`

| Parameter   | Description     | Type     | Required     | Notes     |
|-------------|-----------------|----------|--------------|-----------|
| **domain** | The domain where you need to find the abuse contact info | URL parameter | Required | This is in the format of **example.com**, not **www.example.com** |
| **apikey** | Your ViewDNS API key | URL parameter | Required | | 
| **output** | The output format of the response | URL parameter | Required | **xml** or **json** |


### Sample Response

**JSON response (output=json)**

```json
{
  "query": {
    "tool": "abusecontact_PRO",
    "domain": "example.com"
  },
   "response": {
     "abusecontact": "abuse@example.com"
  }
}
```
<br />

**XML response (output=xml)**

```xml
<?xml version='1.0' encoding='ISO-8859-1'?>
<viewdns>
  <query>
     <tool>abusecontact_PRO</tool>
     <domain>example.com</domain>
  </query>
<response>
    <abusecontact>abuse@example.com</abusecontact>
</response>
</viewdns>
```

| Element | Description | Type | Notes |
|---------|-------------|------|-------|
| **viewdns** | Top level XML only | viewdns data object | | 
| **query** | Query response | JSON object (json) / query data object (xml) | |
| query/**tool** | Name of lookup tool | string | Tool name is **abusecontact_PRO** |
| query/**domain** | Domain queried | string | URL of the domain name queried |
| **response** | The API response | JSON object (json) / response data object (xml) | |
| response/**abusecontact** | E-mail address of the abuse contact for the domain | string | |

<br />

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

---

## Status Codes and Errors 

|     Code    | Description     |  Notes       |
|-------------|-----------------|--------------|
|  **200**    |    OK           |  The API will return a 200/OK for everything **except** a 404/Not found  |
|  **404**    |    Not found    |  API endpoint not found  |

