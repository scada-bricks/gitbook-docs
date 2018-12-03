---
description: 'Contract names: configurable-service and config-service'
---

# Configurable Service

## Configurable-service

This **core contract** defines a simple interface to allow services to be configured and updated remotely.  This allows for centrally managed configuration via a service implementing the **config-service** contract.

Individual services receive the specific configuration they need by implementing the `set-config` end point in their http interface.  This config contains all the options for the target service to run.

## Mandatory methods

All services must support the following methods

{% api-method method="post" host="/set-config" path="" %}
{% api-method-summary %}
set-config
{% endapi-method-summary %}

{% api-method-description %}
This method is called by a **Config Service** on service startup and subsequently any time the config changes.  Every service is responsible for receiving its config in JSON via this method, and updating or restarting.  
  
**Config Services** are covered in more detail later on.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="config" type="object" required=true %}
The config for the target service
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

## Config-service

Config services are responsible for setting and updating the configuration for some or all services. They will generally incorporate links to some form of persistence \(such as a database or key/value store\).

The reason to use a centralised config service is to easily facilitate updates to the config for any running services. This could be adding new devices, increasing or changing the collected tags etc.

The config service itself is responsible for retrieving all the config, and pushing it out to the individual services, and therefore config services know about the existence of all all the services that it is responsible for. All the target services must implement the **configurable-service** contract.

The config service itself doesn't need to implement any contact, and therefore it may not have an HTTP api.  Though often a config service will implement **configurable-service** contract itself, to enable applications to communicate with it and manipulate the whole installations configuration.

