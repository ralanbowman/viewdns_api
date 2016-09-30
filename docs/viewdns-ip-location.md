## Find IP address location

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

