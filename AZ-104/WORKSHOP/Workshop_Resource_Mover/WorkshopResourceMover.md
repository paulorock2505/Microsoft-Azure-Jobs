# AZ-104-LAB-MOD-03
Repositório do Laboratório do módulo 01 para o exame de certificação AZ-104. (Credits by TFTEC)

<h2>Movendo uma VM de região com o Azure Resource Mover</h3>

<h3>Azure Resource Mover</h3>

Recursos que podem ser movidos: 

- Azure Vms e discos associados 
- NICs
- Availability Sets
- Azure Virtual networks 
- Public IP Address 
- Network Security Groups 
- Internal and public load balancers 
- Azure SQL databases and elastic pools

Etapas para movimentação de recursos entre regiões: 

![image](https://user-images.githubusercontent.com/107069287/189147459-9007a8f1-c108-4e57-a4bf-49062b4d1172.png)

Criação dos recursos: 

No portal do Azure criaremos o primeiro grupo de recursos. 

Acesse o portal e no campo de pesquisa digite Resource Group: 

![image](https://user-images.githubusercontent.com/107069287/189152794-100e6d05-97a3-46b3-9af7-dd8ebde2bd1b.png)

Clique em + Create: 

![image](https://user-images.githubusercontent.com/107069287/189152912-f014c0c9-8246-42a3-8249-3bd53e7dc8e5.png)

Criaremos o recurso com o nome RG-Origem na localização de East US: 

![image](https://user-images.githubusercontent.com/107069287/189153281-c6d22d8b-b773-4c69-9b22-310bb6efa92c.png)

No campo tag não preencheremos nada: 

![image](https://user-images.githubusercontent.com/107069287/189153375-d222a025-0b5e-4519-987b-390e9919d048.png)

Na sequência clique em Next, depois Review + Create e depois create. 

![image](https://user-images.githubusercontent.com/107069287/189153603-092594d1-7448-45e8-85a5-c50adb149af6.png)

Na sequência criaremos o resource group de Destino. 

Ainda dentro da aba Resource Manager, clique + Create: 

![image](https://user-images.githubusercontent.com/107069287/189154065-4aa548af-41aa-46d5-9cbe-e93b852a9903.png)

Crie um Resource Group com nome de RG-Destino e localizado no Brazil South: 

![image](https://user-images.githubusercontent.com/107069287/189154323-a8581132-0ff5-41af-9ecd-6fb7d38db2f2.png)

Clique e Review + Create e em seguida create: 

![image](https://user-images.githubusercontent.com/107069287/189154473-230a36c6-49e2-4456-b8fb-66de8a013b5e.png)

Na sequência criaremos os dois virtual networks. 

No portal do Azure, no campo de pesquisa, digite virtual network: 

![image](https://user-images.githubusercontent.com/107069287/189155030-d1d20481-f625-4ac0-83c3-eeba3462855a.png)

Clique em + Create para criarmos as virtual networks: 

![image](https://user-images.githubusercontent.com/107069287/189155331-1da12d8a-8d05-4bd3-9879-979b4f42295b.png)

Primeiro criaremos a Virtual Network (VNET) de origem. 

Na primeira tela em Basics preenchemos o campo Resource Groups com o recurso que criamos RG-Origem e colocaremos o nome de VNET-Origem:

![image](https://user-images.githubusercontent.com/107069287/189155956-97a07cf3-4414-490a-9178-93f53a89b954.png)

Em IP Address manteremos as configurações padrão, sugerida pela plataforma e clicaremos em next: 

![image](https://user-images.githubusercontent.com/107069287/189156168-2958b2ec-599d-4578-a276-0adaac4e71d6.png)

Mantenha as configurações default em security e clique a seguir em Review + Create: 

![image](https://user-images.githubusercontent.com/107069287/189156388-9b92116e-803f-4b57-8320-5436a50ef7f7.png)

A seguir clique em create para criar a VNET. 

Aguarde até a conclusão do processo de criação para não ter overlap de rede. 

Acessaremos novamente a aba de virtual network e criaremos a segunda vnet. 

Clique novamente em + Create: 

![image](https://user-images.githubusercontent.com/107069287/189157524-3c6bea42-356f-4c5a-999b-fc4af9595a11.png)

Na guia basic selecionaremos o Resource Group RG-Destino e nomearemos a Vnet de VNET-Destino: 

![image](https://user-images.githubusercontent.com/107069287/189157864-dba2d9f2-2411-4fba-ad03-05e6f406f506.png)

Clique em Next. 

Na aba IP Address note que o ip está diferente do que configuramos anteriormente. Novamente mantemos as configurações default e clicamos em next. 

![image](https://user-images.githubusercontent.com/107069287/189158423-8ebf84fb-d8d9-4691-9e38-71c6f8df971a.png)

Clique em Review + Create e em seguida create para criarmos a VNET. 

![image](https://user-images.githubusercontent.com/107069287/189158594-96915ca7-eb90-4fbd-beef-7fa941328616.png)

Na sequência criaremos as máquinas virtuais. 

Novamente na tela principal do portal, no campo pesquisa, digite Virtual Machines: 

Clique em + Create e em seguida Azure Virtual Machines: 

![image](https://user-images.githubusercontent.com/107069287/189159297-9dfc2d63-e4eb-49b0-90cc-6f4a7846ed7f.png)

Preencheremos os campos a seguir conforme a imagem abaixo: 
OBS: O grupo de recursos usado nessa etapa será o RG-Origem. 

![image](https://user-images.githubusercontent.com/107069287/189160209-e16d9672-8fe8-4369-b8d2-a04a79b03ee0.png)

Preencha o usuário e senha de sua preferência: 

![image](https://user-images.githubusercontent.com/107069287/189160374-aa0ff296-51e8-4337-9a50-d9eea1ab3df8.png)

Clique em Next. 

Em Disks iremos configurar com as opções sugeridas pela plataforma, podemos seguir clicando em Next: 

![image](https://user-images.githubusercontent.com/107069287/189160722-ff09330f-3c38-4362-a71f-6abfbdeca22c.png)

Valide apenas as configurações que foram associadas e clique em Next: 

![image](https://user-images.githubusercontent.com/107069287/189161090-3b8b353a-87a0-42aa-9962-c9b28f5e6f67.png)

Em management clique novamente em Next para manter as configurações default: 

![image](https://user-images.githubusercontent.com/107069287/189161234-a95d2f04-6a0c-45a7-b2bf-ddd1dc487ec4.png)

Em monitoring na opção Boot Diagnostics marque a opção disable: 

![image](https://user-images.githubusercontent.com/107069287/189161431-c873337d-b619-4706-9444-9c660e588176.png)

Pode clicar na sequência em Review + Create e em seguida create para criarmos a Virtual Machine (VM): 

![image](https://user-images.githubusercontent.com/107069287/189161695-655e05a1-8eaa-4212-a527-15853a554e31.png)

Assim que VM for criada clique em go to resource: 

![image](https://user-images.githubusercontent.com/107069287/189164007-a2df6e91-e596-4bb7-88a2-d107fec9440e.png)

Em seguida rodaremos o script abaixo: 

![image](https://user-images.githubusercontent.com/107069287/189164187-74b6f9e1-5ee8-405d-8b50-ae61c9986c5f.png)

Na aba lateral, role a barra até Operations e vá em Run Command: 

![image](https://user-images.githubusercontent.com/107069287/189164392-0592dff0-19dc-4089-8ebf-cd848aa931eb.png)

Em seguida clique em RunPowerShellScript: 

![image](https://user-images.githubusercontent.com/107069287/189164538-2a8627d9-80a1-4ff2-bcde-c62e5f4f258f.png)

Em seguida cole o script na tela de Power Shell Script para instalarmos IIS e aguarde até a conclusão da execução do comando: 

![image](https://user-images.githubusercontent.com/107069287/189165439-c81f947f-2a14-4a26-97c2-52809de04a4a.png)

Na sequência iremos liberar o acesso a porta 80 na máquina para visualizarmos a página que criamos. 

No portal, na aba de pesquisa vá novamente em Virtual Machine: 

![image](https://user-images.githubusercontent.com/107069287/189165988-3559e9c5-fa56-4c07-ba02-2d1ce64f6194.png)

Clique em VM-Mover (Máquina que criamos logo acima):

![image](https://user-images.githubusercontent.com/107069287/189166290-849284b5-1e63-4c05-be51-301eef4c5505.png)

Na aba ao lado, no campo Settings, clique em Networking:

![image](https://user-images.githubusercontent.com/107069287/189166255-e4aeb8ca-3df2-4fb3-ab28-e14ec933c356.png)

Clique em Add inbound port:

![image](https://user-images.githubusercontent.com/107069287/189166447-cb78e8d2-a126-43d6-8135-ec7def0e7a92.png)

Criaremos a regra conforme a imagem para o ip de destino configurado na máquina: 

![image](https://user-images.githubusercontent.com/107069287/189166936-4e7fea26-4ae1-4c3e-aacc-1d0ba7015015.png)
![image](https://user-images.githubusercontent.com/107069287/189167115-aab7fec4-9660-4533-b471-1f3d83cfd83f.png)

Clique em add. 

Script: 

#Install IIS 
Install-WindowsFeature -name Web-Server -IncludeManagementTools

#Remove default him file 
remove-item C:\inetpub\wwwroot\iisstart.htm

#Add custom hrml file 
Add-Content -Path "C:\interpub\wwwroot\iisstart.htm" -Value $("Live Azure Resource Mover -")































