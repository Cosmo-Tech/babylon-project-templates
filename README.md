# Babylon deployment project templates

## Prequisities
- Have a working Cosmo Tech platform

## How to

### Fill Vault state from Terraform state
Quick guide of [backend-tf-state-to-vault](https://github.com/Cosmo-Tech/backend-tf-state-to-vault)

#### Installation
```
git clone git@github.com:Cosmo-Tech/backend-tf-state-to-vault.git
python3 -m venv ~/backend-tf-state-to-vault
source ~/backend-tf-state-to-vault/bin/activate
pip install -r requirements.txt
```

#### Usage
> Fill all the values below according to your environment
```
export VAULT_ADDR="vault_url"
export VAULT_TOKEN="vault_root_token"
export TENANT_ID="azure_tenant_id"
export ORGANIZATION_NAME="vault_org_name"
export CLUSTER_NAME="kunernetes_cluster_name"
export PLATFORM_NAME="ns_platform_id"
export PLATFORM_ID="ns_platform_id"
export TFSTATE_BLOB_NAME="terraform_state_infra-id"
export STORAGE_ACCOUNT_NAME="storage_account_name"
export STORAGE_ACCOUNT_KEY="storage_account_key_to_get_from_Azure"
export STORAGE_CONTAINER="container_hosting_terraform_states"
```
```
source ~/backend-tf-state-to-vault/bin/activate
```
```
python main.py config write --resource all --use-azure --engine v1 --platform-id ns_platform_id
```

### Babylon 
#### Installation
```
git clone git@github.com:Cosmo-Tech/Babylon.git
python3 -m venv ~/babylonenv
source ~/babylonenv/bin/activate
pip install -r requirements.txt
```

#### Usage
##### Connection
> Fill all the values below according to your environment
```
export BABYLON_ORG_NAME="vault_org_name"
export BABYLON_TOKEN="vault_root_token"
export BABYLON_SERVICE="vault_url"
```
```
babylon namespace use -c ns_context -p ns_platform_id -s state_id
```

##### Create
Organization
```
babylon apply --organization --var-file variables.yaml project/
```
Solution
```
babylon apply --solution --var-file variables.yaml project/
```
Webapp
```
babylon apply --webapp --var-file variables.yaml project/
```
Workspace
```
babylon apply --workspace --var-file variables.yaml project/
```

##### Update
Organization *(same command as creation)*
```
babylon apply --organization --var-file variables.yaml project/
```
Webapp *(same command as creation)*
```
babylon apply --webapp --var-file variables.yaml project/
```
Solution *(same command as creation)*
```
babylon apply --solution --var-file variables.yaml project/
```
Workspace
```
babylon apply --workspace --payload-only  --var-file variables.yaml project/
```

<br>
<br>

**Made with :heart: by Cosmo Tech DevOps team**
 