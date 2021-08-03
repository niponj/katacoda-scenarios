
Terraform builds a graph of all your resources, and parallelizes the creation and modification of any non-dependent resources. Because of this, Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.

A directed graph of dependencies can be show using the CLI:

`terraform graph`{{execute}}

The directed graph of dependencies looks like:

![example graph.png](/bhood4/scenarios/tf101/assets/graph.png)

An image like this visualizing can be made using graph and ![dot](https://en.wikipedia.org/wiki/DOT_(graph_description_language))

`terraform graph| dot -Tpng > /home/scrapbook/tutorial/www/graph.png`{{execute}}

The nginx dashboard on the right shows the graph.png image in index.html 
