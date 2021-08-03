
## A quick quiz

>>Q1: What command line is used to have terraform compare your current project state and show what the delats are to the desired state? <<
=~= plan

>>Q4: Local state storage is appropriate for most development scenarios <<
() True
(*) False

>>Q3: When managing config .tf files <<
[ ] any file in the directory with a .tf is used, so use whatever name you like
[*] all files in the directorry with .tf extension are used, but stick to standard files names like main.tf and variables.tf
[ ] you can use any filenames you like as long as you use vi to edit them
[ ] you must use the filenames main.tf or terraform will not recognized your configuration 

>>Q4: With respect to providers in terraform: <<
( ) you can only use a single provider in your project and can only manage docker resourcest
( ) you can use a limited list of providers to manage various IaaS, PaaS, and SaaS, but only one per project
( ) you can use multiple standard providers in the same project to manage various IaaS, PaaS, and SaaS, but only one provider per project
( ) you can use multiple standard or custom providers in the same project, and even have mulitple instances of a single provider per project
