# Create an Instace of Azure Container Registry (ACR) 
1. open Cloud sheel and open bash
2. Run az group list  -- to list all resource groups
3. Copy the resouce group name
4. Setup there variables as follows
    a. rg=<resourceGroupname> - copied from Step 2
    b. name=acrlabdemo
    c. acr="$name$RANDOM"
5. az acr create --resource-group $rg --name $acr --sku Basic
6. Once ACR is created, enable admin user for the registry by running below command
    az acr update -n $acr --admin-enabled true