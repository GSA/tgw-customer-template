# Circle CI 

## Overview <a name="s1"></a>

This CircleCI Pipeline is controlled by the config.yml file.
The purpose of this pipeline is to build,test, and deploy the TGW AWS infrastructure using CloudFormation and Terraform IAC.

## Table of Contents <a name="s2"></a> 

* [Overview](#s1)
* [Table of Conents](#s2)
* [Environment Variables](#s3)
* [Commands](#s3.1)
* [Jobs](#s4)
* [Work Flows](#s5)


## Environment Variables <a name="s3"></a>

* Note: All variables are of the type `string`.

Encrypted variables set in the CircleCI Environement variables GUI.

| Variable    |  Description    | 
|---        |---              | 
| AWS_ACCESS_KEY_ID_dev | Access Key ID needed by IAC deployment for the Dev environment. | 
| AWS_SECRET_ACCESS_KEY_dev |  Access Key Secret needed by IAC deployment for the Dev environment.  |  
| AWS_ACCESS_KEY_ID_master | Access Key ID needed by IAC deployment for the Dev environment. | 
| AWS_SECRET_ACCESS_KEY_master |  Access Key Secret needed by IAC deployment for the Dev environment.  |  


Variables set in the `setup-environment-vars` job

| Variable    |  Description    | 
|---        |---              | 
| var name | ????| 



## Commands <a name="s3.1"></a>

### setup-environment-vars

Sets up required environment variables.  Used to allow for variable interpolation.
  
### cloudformations

Validate and deploy CloudFormation templates.

#### parameters:
| Parameter   |  Description    | Options | Type | 
|---        |---              |---   |---  | 
| cf_command | What type of command to run | validate, deploy  | string |
| stack_name | What is then name of the stack | any string | string | 
| template_path | Path to template | ***file*** relative path from repo root | string |                                
| parameter_overrides | Parameters for template |  Example: "Key1=Value1 Key2=Value2" | string |
| tags | Parameters for resources |  Example: "Key1=Value1 Key2=Value2" | string |


### run-terraform

Run terraform commands to init, validate, plan and apply.

#### parameters:
| Parameter   |  Description    | Options | Type | 
|---        |---              |---   |---  | 
| run_command | What type of command to run | validate, plan, deploy  | string |
| also_destroy | Do you want to destroy after running apply | true, false | string | 
| terraform_dir | Path to terraform code | ***directory*** relative path from repo root | string |                               


### dependency-prep

Download dependency files and run any commands required to make them ready for deployment.



## Jobs <a name="s4"></a>


### job name

description

## Workflows <a name="s5"></a>


### build_and_deploy

description