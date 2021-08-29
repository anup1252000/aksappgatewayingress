# aksappgatewayingress
1. Create Vnet with 2 subnet(10.0.0.0/16)
        a) aks(10.0.0.0/24)
        b) app gateway(10.0.1.0/27)
2. Create AKS with Azure network policy-> select Vnet and aks subnet
3. Create APP Gateway 
          - create public IP
          - Create non targeted backend pool
          - Set http routing rule. everything default
4. Run the addon in powershell or vs code
          `code` $appgwid=$(az network application-gateway show -n <app gateway name> -g <resource group> -o tsv --query "id")
          `code` az aks enable-addons -n <Kubernetes cluster> --appgw-id $appgwid -g <resource group> -a ingress-appgw  
  5. Run our yaml file. In this example frontend.yaml and ingress.yaml(run ingress file where the frontend.yaml namespace resides)
  6. run kubectl get ingress and copy the address & execute it in postman/browser.
