<h2>Lab 03 - Manage Azure Resources with PowerShell</h2> 

<h3>Lab scenario:</h3> 

Agora que você explorou os recursos básicos de administração do Azure associados ao provisionamento de recursos e organizou-os com base em grupos de recursos usando o portal do Azure e os modelos do Azure Resource Manager, deseja as tarefas equivalentes com o Azure Power Shell. Para evitar a instalação dos módulos do Azure PowerShell, você aproveitará o Azure Cloud Shell. 

<h3>Objetivos:</h3> 

<table border="1">    
  <tr>
    <th colspan="1">Tarefa 1:</th>  	              
    <th colspan="2">Instalar Azure PowerShell localmente e conectar na sua subscrição do Azure.</th>
  </tr>
<td>Tarefa 2:</td>
    <td>Criar um Resource Group, uma VNET e uma Subnet.</td>
  </tr>
  <tr>
    <td>Tarefa 3:</td>
    <td>Iniciar uma sessão do PowerShell no Cloud Shell do Azure e criar uma VM.</td>
  </tr>
 </table>
 
 <h3>Task 1:	Instalar Azure PowerShell localmente e conectar na sua subscrição do Azure</h3>

<table border="1">    
  <tr>
    <th colspan="1">PowerShell</th> 
</table>

- O Azure PowerShell funciona com o <b>PowerShell 6.2.4 e posterior em todas as plataformas.</b> 
- Ele também é compatível com o <b>PowerShell 5.1 no Windows.</b> 
- O Azure PowerShell não tem requisitos adicionais quando executado no <b>PowerShell 6.2.4 e posterior.</b>
- Para verificar sua versão de PowerShell utilize o seguinte comando: <b>$PSVersionTable.Version.</b>
- Instale o <b>.NET Framework 4.7.2 ou posterior.</b>
- Baixar o PowerShell v7.0.3: <b>https://github.com/PowerShell/PowerShell/releases/tag/v7.0.3</b>

Validar versão do Powershell:

- $PSVersionTable.PSVersion

Atualizar versão Powershell 7.0.3:
- https://github.com/PowerShell/PowerShell/releases/tag/v7.0.3

Validar versão Net Framework (Validar chave Version)REGEDIT:
- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full

Instalar o módulo de PowerShell:
- Install-Module -Name Az -AllowClobber

Acessar sua subscrição do Azure:
- Connect-AzAccount

Atualizar seu módulo de PowerShell:
- Update-Module -Name Az

Importar Módulo Azure
- Import-Module Az



 
