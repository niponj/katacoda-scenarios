

Terraform works based on configuration files, in this case main.tf. The configuration is a declarative expression of the desired state of your infrastructure. Terraform commands uses all files in the directory that have a .tf extension as configuration input.

The config files use a simple, powerful [HCL templating language](https://www.terraform.io/docs/configuration/syntax.html)

A resource is a component of your infrastructure associated with a provider. For example a container or image resource from the docker provider is used to manage real containers and images.

We can now start defining the resources of our infrastructure. The first resource is our Docker image. A resource has two parameters, one is a TYPE and second a NAME. The type is docker_image and the name is nginx. Within the block we define the name and tag of the Docker Image.


<pre class="file" data-filename="main.tf" data-target="append">resource "docker_image" "nginx" {
  name = "nginx:1.11-alpine"
}
</pre>

We can define our container resource. The resource type is docker_container and name as nginx-server. Within the block we set the resource parameters. We can reference other resources, such as a the image.

<pre class="file" data-filename="main.tf" data-target="append">resource "docker_container" "nginx-server" {
  count = "${var.container_count}"
  name = "nginx-server-${count.index+1}"
  image = "${docker_image.nginx.latest}"
  ports {
    internal = 80
  }
  volumes {
    container_path  = "/usr/share/nginx/html"
    host_path = "/home/scrapbook/tutorial/www"
    read_only = true
  }
}
</pre>

* HCL templating supports "interpolation" of values in other resources, such as the docker_container resource referencing image = "${docker_image.nginx.latest}"

* Count makes it easy to create multiples of resources - this example runs the container container_count times. Resources with count can be accessed as list elements in HCL "interpolation" 

See more information on [HCL functions and interpolation](https://www.terraform.io/docs/configuration-0-11/interpolation.html)
