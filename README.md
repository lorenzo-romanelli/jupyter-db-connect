# Jupyter to Azure Databricks connector
Connect to Azure Databricks clusters from Jupyter notebooks.

## Installation

### 1. Clone this repo
```bash
$ git clone https://github.com/lorenzo-romanelli/jupyter-db-connect.git
```

### 2. Create and activate a virtual environment
```bash
$ cd jupyter-db-connect
$ virtualenv env
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
* `Cluster ID` (see [here](https://docs.databricks.com/user-guide/faq/workspace-details.html#cluster-url))
* `Org ID` (see `?o=orgId` in your Databricks URL)
* `Port`: here you can use port 8787 since we are working on Azure

## Run tests
Run the following command to test your setup is up and working:
```bash
$ databricks-connect test
```

If the configured Databricks cluster is not running, it will start automatically (it might take some time).

## Enjoy!
Run the following command:
```bash
$ jupyter notebook
```
And from your browser navigate to `localhost:8888`.

## Example notebook
The notebook `test notebook.ipynb` contains some example commands to set up your Databricks environment from Jupyter itself.

For example, it defines your `SparkContext`, as well as `dbutils` and the `sqlContext`. 

On Databricks they are automatically defined, but they need to be manually created in your local Jupyter notebook.
