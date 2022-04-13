### OCI Function - Criação e Configuração

Aqui vamos abordar toda a estrutura necessária para que possamos criar nossa aplicação function. Os tópicos abordados nessa sessão são:

* [Criação do Application](https://github.com/heloisaescobar/OCI_Function/blob/main/OCI%20Function%20-%20Cria%C3%A7%C3%A3o%20e%20Configura%C3%A7%C3%A3o.md#cria%C3%A7%C3%A3o-do-application)
* [Criação do Function](https://github.com/heloisaescobar/OCI_Function/blob/main/OCI%20Function%20-%20Cria%C3%A7%C3%A3o%20e%20Configura%C3%A7%C3%A3o.md#cria%C3%A7%C3%A3o-do-function)
* [Preparação do Script](https://github.com/heloisaescobar/OCI_Function/blob/main/OCI%20Function%20-%20Cria%C3%A7%C3%A3o%20e%20Configura%C3%A7%C3%A3o.md#prepara%C3%A7%C3%A3o-do-script)
* [Invocação do Script](https://github.com/heloisaescobar/OCI_Function/blob/main/OCI%20Function%20-%20Cria%C3%A7%C3%A3o%20e%20Configura%C3%A7%C3%A3o.md#invoca%C3%A7%C3%A3o-do-script)
* [Visualizar Resultados](https://github.com/heloisaescobar/OCI_Function/blob/main/OCI%20Function%20-%20Cria%C3%A7%C3%A3o%20e%20Configura%C3%A7%C3%A3o.md#visualizar-resultados)

#### Criação do Application

Para criarmos nosso compartimento, seguir os passos abaixo:

Acessar o menu de hamburguer -> Developer Services -> Applications
![image](https://user-images.githubusercontent.com/46925501/163269798-a98903c4-873c-4bed-b7bb-f00fdb79949f.png)

Acessar o tópico <i>Applications</i> e clicar em <i>Create Application</i>
![image](https://user-images.githubusercontent.com/46925501/163270104-f00b61c9-56d4-4594-b229-8b3175005230.png)

Preencher formulário conforme imagem abaixo e clicar em <i>Create</i>
![image](https://user-images.githubusercontent.com/46925501/163270506-aaaf2d07-4bb5-407f-b4a4-7ec5d2f9f2b3.png)

#### Criação do Function

Finalizada a criação da sua aplicação, vamos iniciar a configuração do nosso function. Para isso acessar a aplicação que você criou no passo anterior:
![image](https://user-images.githubusercontent.com/46925501/163270846-5448901a-28b1-4de7-8cb5-b41dda8fb576.png)

Temos duas opções de configurar nosso function, via <i>Cloud Shell Setup</i> ou <i>Local Setup</i>. Para nosso laboratório, vamos selecionar a opção <i>Cloud Shell Setup</i>
![image](https://user-images.githubusercontent.com/46925501/163271105-a9ba5d65-8874-4ece-b030-7bc6bcdbbd88.png)

Clicando em <i>Cloud Shell Setup</i>, vamos visualizar uma sequência de passos que deverão ser seguidos para que nosso function seja provisionado, contudo se atentar nos próximos comentários, pois vamos fazer algumas alterações.

- <b>Passo 5 - Generate an Auth Token </b>
Acessar o link fornecido no procedimento. Na sessão <i>Auth Tokens</i> clicar em <i>Generate Token</i>
![image](https://user-images.githubusercontent.com/46925501/163271763-68924f94-facf-41ae-b928-728704b36e1d.png)

Preencha o Formulário com o Descritivo do seu token e clique em <i>Generate Token</i>
![image](https://user-images.githubusercontent.com/46925501/163271900-a9f2b2ce-244c-4747-a3f0-578ddfd053bf.png)

Irá aparecer a tela abaixo. <b>ATENÇÃO</b>: Copie o token apresentado e armazene em local seguro, pois o mesmo não será possível visualizar novamente.
![image](https://user-images.githubusercontent.com/46925501/163272087-0d3d65f2-420b-49b6-a04e-14b84cf279e7.png)

- <b>Passo 5 - <i>Log into the Registry using the Auth Token as your password</i> </b>
Execute o comando apresentado na tela do passo 5, ele irá solicitar um password. O password é o token gerado no passo 5.
![image](https://user-images.githubusercontent.com/46925501/163272720-a5174493-43cd-42a1-9d5f-20f8b55d1bc5.png)

- <b>Passo 8 - Generate a 'hello-world' boilerplate function</b>
Para o passo 8 vamos fazer algumas alterações, primeiro não vamos criar uma aplicação java e sim <b>Python</b> e também, vamos criar uma aplicação com o nome que desejar =]
> fn init --runtime python fn_get_app_coffee

Por hora vamos parar no passo 8 e seguir com o próximos passos desse material.

#### Preparação do Script

Agora vamos preparar a aplicação que vamos executar no nosso function. Para isso fazer download do arquivo [func.py](https://github.com/heloisaescobar/OCI_Function/blob/main/func.py)

Feito o download do passo anterior, vamos abrir o arquivo em nosso editor de preferência e vamos fazer uma alteração na linha <b>27</b>.

Se lembram do passo [Criação Bucket - Object Storage](https://github.com/heloisaescobar/OCI_Function/blob/main/Cria%C3%A7%C3%A3o%20Bucket%20-%20Object%20Storage.md), então vamos pegar o nome desse bucket criado e adicionar na linha 27!

Salvem o arquivo!

Agora que alteramos essa linha, vamos voltar para o Cloud Shell (Telinha Preta!), e fazer o upload do arquivo que acabamos de editar.

Para isso clicar no menu de hamburguer do Cloud Shell e depois <i>Upload</i>
![image](https://user-images.githubusercontent.com/46925501/163274907-f4e6e697-7ce5-45be-9ea7-792bc0ee7fba.png)

Selecione o arquivo e depois <i>Upload</i>
![image](https://user-images.githubusercontent.com/46925501/163275051-0448ebfb-c491-4716-b7b0-14b90169282d.png)

Agora se vocês executarem o comando ls do Linux, vamos visualizar um arquivo e um diretório, como a imagem a seguir
![image](https://user-images.githubusercontent.com/46925501/163275189-2ab82837-e7f4-47f9-81a8-014813853530.png)

Será necessário enviarmos o arquivo que fizemos upload para o diretório da nossa aplicação. Para isso executar o comando abaixo
> mv func.py fn_get_app_coffee/

Se caso perguntar se você deseja sobrescrever um arquivo existente, pode confirmar.

Agora que criamos o arquivo da nossa aplicação, vamos fazer o deploy dela, para isso voltamos ao <i>Cloud Shell Setup</i>, e vamos executar apenas o passo <b>9</b> e passo <b>10</b>

#### Invocação do Script

Após finalizarmos os passos anteriores, vamos invocar nossa aplicação, para isso executamos o Passo 11 do <i>Cloud Shell Setup</i>
> fn invoke get_api_app <i>NOME_DO_SEU_FUNCTION</i>

Finalizando com sucesso, vamos obter um resultado parecido com a imagem a seguir
![image](https://user-images.githubusercontent.com/46925501/163276975-ae57bf55-3c41-4c88-a574-6ce142c2b003.png)

#### Visualizar Resultados

Após finalizarmos com sucesso, podemos consultar nosso Bucket no object Storage para verificar se nosso arquivo foi criado com sucesso.
![image](https://user-images.githubusercontent.com/46925501/163277510-d33efcd5-bb8d-4d28-8b65-37ef1f61bada.png)


