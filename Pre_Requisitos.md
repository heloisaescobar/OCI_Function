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

3ª function_bucket_policy
Name: 
Descriotion:
Compartment:
Policy Builder:

#### Criação Dynamic Group
