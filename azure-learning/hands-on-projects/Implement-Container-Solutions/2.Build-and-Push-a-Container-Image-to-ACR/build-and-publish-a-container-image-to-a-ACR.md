# Build and Push a Container Image to ACR
-- Adding a container Image to to Registry
1. navigate to a clouddrive/any directory
2. create a simple docker file by running below command
    echo FROM mcr.microsoft.com/hello-world > Dockerfile
3. build and push the image to ACR using Docker file
   az acr build --image sample/hello-world:v1 --registry $acr --file Dockerfile .