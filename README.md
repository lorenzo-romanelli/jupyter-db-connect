# Jupyter to Azure Databricks connector
Connect to Azure Databricks clusters from Jupyter notebooks.

## Installation

### 1. Clone this repo
```bash
$ git clone https://github.com/lorenzo-romanelli/jupyter-db-connect.git
```

### 2. Create and activate a virtual environment
Remember, when creating the virtual environment you need to install either __Python 2.7__ or __Python 3.5__, depending on which version is running on the cluster.
```bash
$ cd jupyter-db-connect
$ virtualenv -p /usr/bin/python3.5 env
$ cd env
$ source bin/activate
```

### 3. Install requirements
```bash
$ pip install -r requirements.txt
```

## Configure your Databricks connection
Run the following command:
```bash
$ databricks-connect configure
```

And follow the onscreen instructions.
You will be asked to fill in some config values:

* `Databricks Host`, e.g. https://westeurope.azuredatabricks.net
* `Databricks Token` (see [here](https://docs.databricks.com/api/latest/authentication.html#generate-a-token))
* `Cluster ID` (see [here](https://docs.databricks.com/workspace/workspace-details.html#cluster-url))
* `Org ID` (see `?o=orgId` in your Databricks URL)
* `Port`: here you should use port 8787, since we are working on Azure

## Run tests
Run the following command to test your setup is up and working:
```bash
$ databricks-connect test
```

If the remote Databricks cluster is not running, it will start automatically (it might take some time).

## Enjoy!
Run the following command:
```bash
$ jupyter notebook
```
And from your browser navigate to `localhost:8888`.

## Example notebook
The notebook `test notebook.ipynb` contains some example commands to set up your Databricks environment from Jupyter itself, by defining the `SparkContext`, as well as `dbutils` and `sqlContext`. 

On Databricks, they are automatically defined, but they need to be specified by hand in your local Jupyter notebook.
