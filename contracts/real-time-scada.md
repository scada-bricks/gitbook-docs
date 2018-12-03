---
description: 'Contract name: real-time-scada'
---

# Real-time SCADA

The realtime SCADA interface is a simple service that allows read / write of tags from multiple devices

## Definition

{% api-method method="get" host="/read?dataSet=\[dataSetName\]&device=\[device\]&tag=\[tagName\]" path="" %}
{% api-method-summary %}
read
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The response contains the current value of the tag, and the exact time it was returned
{% endapi-method-response-example-description %}

```javascript
{
   "value": "string | bool | number | date",
   "dateTime": "dateTime"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="/write?dataSet=\[dataSetName\]&device=\[device\]&tag=\[tagName\]" path="" %}
{% api-method-summary %}
write
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="value" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

