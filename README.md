# mistral_kubernetes

### About
This project creates mistral workflows which does the following job -:
  - Creates instances on top of openstack cloud (based on user input params such as image type , flavor , network)
  - Captures the IP of instances , SSH to machine
  - Download the script on master first and install kubernetes
  - Create n minion nodes on parallel execution
  - Captures the IP of instances , SSH to machine
  - Download the script on minions and install kubernetes
  - Return the master and minion nodes ip address

### Note 
  - You can create n number of master and minion nodes based on config files `config.mist.yaml`
  - You can specify image , flavor , network type according to your choice
  - You can execute any script of your choice to master group or minion group of servers


### Installation

Setup the python packages, can be done on virtualenviroment as well
```sh
$ pip install -r requirements.txt
```


### Usage

  - Edit the file `config.mist.yaml` containing the params
  - workflow_name = Name of mistral workflow
  - description = Description of workflow
  - minion_nodes = count of Kubernetes minion/slave nodes
  - master_nodes = count of Kubernetes master nodes
  - vm_name_prefix = Name of instances created on openstack ## Work in Progress
  - master_script = Script to be downloaded and executed on master nodes for setting up kubernetes master operation 
  - minion_script = Script to be downloaded and executed on master nodes for setting up kubernetes master operation
  
  ```sh
$ python generate_config.mist.py > my_mistral_workflow.yml
$ mistral workflow-create my_mistral_workflow.yml
$ mistral execution-create workflow_name your_params_file.json
```
