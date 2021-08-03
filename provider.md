

* A provider is an abstract and modular approach for IaaS, SaaS and PaaS vendor integrations

* Each integration is packaged as a provider, which understands the vendor’s APIs and exposes specific resources

* Example providers include docker, azurerm, aws, vmware, datadog

* Multiple providers can be referenced in the same project

* There are many [standard providers](https://www.terraform.io/docs/providers/index.html), as well as a large number of thirdparty custom providers

Providers are configured in terraform config files with a .tf extension, which typically include configuraiton of the API endpoint, credentials, debug settings, and other global parameters for a specific API integration.

This config file defines a docker provider with the host where we want to apply our configuration

<pre class="file" data-filename="main.tf" data-target="replace">provider "docker" {
  host = "unix:///var/run/docker.sock"
}

</pre>

Multiple providers can be referenced in the same project.

Also, multiple instances of a single provider can be used with "alias", for instance with multiple docker hosts or aws regions.

For more info, see [Provider documentation](https://www.terraform.io/docs/configuration/providers.html)
