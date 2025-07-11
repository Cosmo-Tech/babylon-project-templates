# Babylon deployment projects template

## Prequisities
- Have a working Babylon

## How to

```
export BABYLON_ORG_NAME="cosmotech"
export BABYLON_TOKEN="vault_root_token"
export BABYLON_SERVICE="vault_url"
```

```
babylon namespace use -c ns_context -p ns_platform_id -s state_id
```

### First creation
```
babylon apply --organization --var-file variables.yaml project/
babylon apply --solution --var-file variables.yaml project/
babylon apply --webapp --var-file variables.yaml project/
babylon apply --workspace --var-file variables.yaml project/
```

### In case of modification needed
Organization (same command as creation)
```
babylon apply --organization --var-file variables.yaml project/
```
Webapp (same command as creation)
```
babylon apply --webapp --var-file variables.yaml project/
```
Solution (same command as creation)
```
babylon apply --solution --var-file variables.yaml project/
```
Workspace :
```
babylon apply --workspace --payload-only  --var-file variables.yaml project/
```


# Made with :heart: by Cosmo Tech DevOps team
 