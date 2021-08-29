# aksappgatewayingress
Step 1: Create Vnet with 2 subnet(10.0.0.0/16)
        a) aks(10.0.0.0/24)
        b) app gateway(10.0.1.0/27)
 Step 2: Create AKS with Azure network policy-> select Vnet and aks subnet
 Step 3: Create APP Gateway 
          a) create public IP
          b) Create non targeted backend pool
          c) Set http routing rule. everything default
 Step 4: Run the addon in powershell or vs code
          $appgwid=$(az network application-gateway show -n <app gateway name> -g <resource group> -o tsv --query "id")
          az aks enable-addons -n <Kubernetes cluster> --appgw-id $appgwid -g <resource group> -a ingress-appgw  
  Step 5: Run our yaml file. In this example frontend.yaml and ingress.yaml(run ingress file where the frontend.yaml namespace resides)
  Step 6: run kubectl get ingress and copy the address & execute it in postman/browser.
