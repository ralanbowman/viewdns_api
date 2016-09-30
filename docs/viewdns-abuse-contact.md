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


