Related terraform files for a project are place in a common directory. 
In addition to .tf configuration files, other files in the directory include:
* .terraform: Folder containing downloaded provider binaries 
* variables.tf: Consolidated variable initialisation
* outputs.tf: Consolidated outputs
* .tfvars: Variable overrides 

Recommendations
* Keep key components in separate TF project directorys
* Each directory brings a dedicated state file - blast radius stays small
* Follow standardized file naming, e.g. main.tf, varialbes in variables.tf, outputs in outputs.tf

<pre>├── nginx
│   ├── dev.tfvar
│   ├── main.tf
│   └── variables.tf
├── database
│   ├── main.tf
│   ├── mysql.tf
│   ├── variable_overrides.tfvar
│   └── variables.tf
└── network
    ├── main.tf
    ├── net-peering.tf
    ├── variable_overrides.tfvar
    └── variables.tf
</pre>

We have created the directory 'nginx' for the example terraform project and changed into that directory.
