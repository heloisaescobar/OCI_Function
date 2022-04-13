### Pré Requisitos

Aqui vamos abordar toda a estrutura necessária para que possamos criar nossa aplicação function. Os tópicos abordados nessa sessão são:
* [Criação Compartimento](https://github.com/heloisaescobar/OCI_Function/blob/main/Pre_Requisitos.md#cria%C3%A7%C3%A3o-compartimento)
* [Criação VCN - Virtual Cloud Networks](https://github.com/heloisaescobar/OCI_Function/blob/main/Pre_Requisitos.md#cria%C3%A7%C3%A3o-vcn---virtual-cloud-network)
* [Aplicação de Políticas](https://github.com/heloisaescobar/OCI_Function/blob/main/Pre_Requisitos.md#aplica%C3%A7%C3%A3o-de-pol%C3%ADticas)
* [Criação Dynamic Group](https://github.com/heloisaescobar/OCI_Function/blob/main/Pre_Requisitos.md#cria%C3%A7%C3%A3o-dynamic-group)


#### Criação Compartimento

Para criarmos nosso compartimento, seguir os passos abaixo:

Acessar o menu de hamburguer -> Identity & Security -> Compartments
![image](https://user-images.githubusercontent.com/46925501/163200476-d24598d9-8cd6-4e58-8b07-c58237556a16.png)

Acessar o tópico <i>Compartments</i> e clicar em <i>Create Compartment</i>
![image](https://user-images.githubusercontent.com/46925501/163200903-2c52b498-9e9c-4a7f-b4ec-42edc807a3c8.png)

Preencher formulário conforme imagem abaixo e clicar em <i>Create Compartment</i>
![image](https://user-images.githubusercontent.com/46925501/163201450-8a9fc764-8503-48c9-9fa2-3781a41b7544.png)

#### Criação VCN - Virtual Cloud Network

Para criarmos nossa VCN - Virtual Cloud Networkd, seguir os passos abaixo:

Acessar o menu de hamburguer -> Network -> Virtual Cloud Networks
![image](https://user-images.githubusercontent.com/46925501/163201821-e895723b-1f73-4684-8ad7-226a097ab91c.png)

Acessar o tópico <i>Virtual Cloud Networks</i> e clicar em <i>Start VCN Wizard</i>
![image](https://user-images.githubusercontent.com/46925501/163202204-d3aed35e-26e2-4abb-80da-19b1117a3b1e.png)

Confirme se a opção <i>Create VCN with Internet Connectivity</i> está selecionada e clique em <i>Start VCN Wizard</i>
![image](https://user-images.githubusercontent.com/46925501/163202455-f2c317d7-3403-4f89-856f-9eda11e5d443.png)

Preencher formulário conforme imagem abaixo e clicar em </i>Create VCN</i>
![image](https://user-images.githubusercontent.com/46925501/163202801-2c976a85-95a5-4e1b-9c0a-8a59c43dd02c.png)
![image](https://user-images.githubusercontent.com/46925501/163202945-5ec86ccb-be47-4405-9488-be27f529b405.png)

** Caso você já possua uma VCN criada, necessário alterar para outro CIDR (Exemplo:10.1.0.0/16 ou 10.2.0.0/16 entre outros)

#### Aplicação de Políticas

Para aplicarmos nossa políticas de acesso, seguir os passos abaixo:

Acessar o menu de hamburguer -> Identity & Security -> Policies
![image](https://user-images.githubusercontent.com/46925501/163203841-6f4e892f-70aa-4503-a885-2da182f2f9ad.png)

Acessar o tópico <i>Policies</i> e Clicar em <i>Create Policy</i>
![image](https://user-images.githubusercontent.com/46925501/163204345-7480f3d1-8af5-48a7-8fa7-efb37f7eaa90.png)

Vamos criar três grupos de policies, seguindo o formulário a seguir:

![image](https://user-images.githubusercontent.com/46925501/163205677-ce2b65a1-c5de-4890-8716-413bf10bd9d3.png)

1ª Policy: object_storage_policy
Name: object_storage_policy
Description: Policies de acessos e gerenciamento do object storage
Compartment: Necessário que seja no compartmento root
Policy Builder: 
> Allow service objectstorage-sa-saopaulo-1 to manage object-family in tenancy

2ª Policies_faas
Name: Policies_faas
Description: Policies de acesso e gerenciamento para criação do function
Compartment: Necessário que seja no compartmento root
Policy Builder:
> Allow group <SEU_GRUPO> to use cloud-shell in tenancy
> 
> Allow group <SEU_GRUPO> to manage repos in tenancy
> 
> Allow group <SEU_GRUPO> to read objectstorage-namespaces in tenancy
> 
> Allow group <SEU_GRUPO> to manage logging-family in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to read metrics in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to manage functions-family in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to use virtual-network-family in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to use apm-domains in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to read vaults in compartment <SEU_COMPARTIMENTO>
> 
> Allow group <SEU_GRUPO> to use keys in compartment <SEU_COMPARTIMENTO>
> 
> Allow service faas to use apm-domains in compartment <SEU_COMPARTIMENTO>
> 
> Allow service faas to read repos in tenancy where request.operation='ListContainerImageSignatures'
> 
> Allow service faas to {KEY_READ} in compartment Team_Oracle where request.operation='GetKeyVersion'
> 
> Allow service faas to {KEY_VERIFY} in compartment Team_Oracle where request.operation='Verify'

3ª function_bucket_policy
Name: function_bucket_policy
Description: Policies para que o function consiga gerenciar o bucket descrito.
Compartment: <SEU_COMPARTIMENTO>
Policy Builder:
> Allow dynamic-group <SEU_DYNAMIC_GROUP> to manage objects in compartment <SEU_COMPARTIMENTO> where target.bucket.name='<NOME_BUCKET>'

* Para criar e pegar a informação do Dynamic Group, seguir [<SEU_DYNAMIC_GROUP>](https://github.com/heloisaescobar/OCI_Function/blob/main/Pre_Requisitos.md#cria%C3%A7%C3%A3o-dynamic-group)
* Para criar e pegar a informação do Nome Bucket, seguir [<NOME_BUCKET>](a)

#### Criação Dynamic Group

Para criarmos nosso Dynamic Group, seguir os passos abaixo:

Acessar o menu de hamburguer -> Identity & Security -> Dynamic Groups
![image](https://user-images.githubusercontent.com/46925501/163208658-4d6d8878-4b7f-4220-8d1a-44c1bf06b522.png)

Acessar o tópico <i>Dynamic Groups</i> e clicar em <i>Create Dynamic Group</i>
![image](https://user-images.githubusercontent.com/46925501/163209058-71a0a33c-5084-4dd7-a9b5-bc8d93f4a54d.png)

Preencher formulário conforme imagem abaixo e clicar em <i>Create</i>
![image](https://user-images.githubusercontent.com/46925501/163211406-3b101e97-f481-4b69-807e-6a23bc5f443f.png)

Informações Dynamica Group:
Name: A escolha (Importante ser de fácil identificação - Exemplo: DynGroup_Team)
Descrição: Dynamic Group Team
Rule:
> All {resource.type = 'fnfunc', resource.compartment.id ='<COLETAR_OCID_DO_SEU_COMPARTMENTO>'}

Para pegar a informação do OCID do seu compartmento, seguir <COLETAR_OCID_DO_SEU_COMPARTMENTO>

### Coletando OCID do seu Compartmento

Acessar o menu de hamburguer -> Identity & Security -> Compartments
![image](https://user-images.githubusercontent.com/46925501/163212632-547b1971-a873-4d2a-8250-0c1194ad3954.png)

Acessar o tópico Compartments e você irá ver a lista de compartimentos criados em seu ambiente. Identifique o seu compartmento.
Na coluna OCID, você identifica o ID do seu compartimento, copie e armazene para utilizar quando necessário.
![image](https://user-images.githubusercontent.com/46925501/163212921-04db9c6e-a8c1-4086-bef8-1f3202b87f9c.png)



