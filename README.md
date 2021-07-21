# POC_Keycloak_LDAP-AD-

Poc Keycloak utilizando o LDAP para simular um Active Directory (escopo Windows)

O objetivo dessa POC é simular um Active directory utilizando a ferramenta LDAP admin e integrar com o Keycloak que é uma ferramenra de Single Sign on (SSO), e o MySQL que é para armazenarmos as credenciais.

### Instalando LDAP, Keycloak e mysql

1 - Vamos instalar as aplicações, então, execute o arquivo dockercompose.yaml em sua IDE de preferência ou até mesmo no seu terminal utilizando o comando **docker-compose up -d** , isso executará o deploy das aplicações.

Para validar se os containers estão up e funcionais execute o comando **docker ps** ou **docker-compose ps**. 

![image](https://user-images.githubusercontent.com/68164552/126538928-ac4489c3-be49-476d-8b40-58569687fbc3.png)

Feito todos esses passo vamos validar se a aplicação do keycloak esta no ar.

### Validando Keycloak

Ao executar vá em seu navegador de preferência e digite: localhost:8080

O esperado é acessarmos a tela de adm do Keycloak.

![image](https://user-images.githubusercontent.com/68164552/126539682-faf8a698-78c5-4811-9d31-5cf65d5d0861.png)


### Configurando o Keycloak

Mediante ao acesso acima clicamos em console administration

![image](https://user-images.githubusercontent.com/68164552/126540129-49228d2d-554a-4387-8107-1bccf48515ce.png)

Defina um usuário com email e senha

![image](https://user-images.githubusercontent.com/68164552/126541518-daa8efb1-0680-4a5b-a362-4260e135fe01.png)

Após logar na ferramenta na tela de configuração defina as configurações para o REALM

Obs: Como é uma POC estamos utilizando o REALM master, porém é recomendavel que você crie um novo.

![image](https://user-images.githubusercontent.com/68164552/126544122-34cdf42f-3c9f-4918-8eef-4b9c594f7dbf.png)

Em user federation execute as seguintes configurações.

![image](https://user-images.githubusercontent.com/68164552/126543939-0a6cac77-aa8c-4f36-aa47-6c617e4a2cc1.png)

Obs: algumas senhas estão no arquivo de Manifesto "dockercompose.yaml"

### Iniciando a configuração do servidor LDAP

1 - Vamos baixar o binário portable do LDAP utilizando o seguinte link http://www.ldapadmin.org/download/ldapadmin.html
2 - Execute o Binário como admonistrador. abaixo o esperado.
![image](https://user-images.githubusercontent.com/68164552/126544663-36868905-a078-48bb-a21b-fe685558a84f.png)
3 - Clique na imagem do servidor.
![image](https://user-images.githubusercontent.com/68164552/126545015-de64fc97-6b26-4123-9da9-6d2f59a89ded.png)

4 - Defina as seguintes configurações e clique em test connect.
![image](https://user-images.githubusercontent.com/68164552/126545169-b25d8b6d-4092-4370-b644-7061e0a34e1d.png)

5 - Após Isso o Keycloak esta integrado com o LDAP.

### Validando configurações e criando um usuário

Por enquanto estamos somente como o usuário admin.

![image](https://user-images.githubusercontent.com/68164552/126545814-c6f1d2d1-42a7-42b2-aa76-f61bcd3de1d1.png)

Vamos criar um usuário no LDAP e sincronizar com o Keycloak 

![image](https://user-images.githubusercontent.com/68164552/126547013-16f08480-2cf6-4b07-8300-fba6240574f9.png)

Usuário criado.

![image](https://user-images.githubusercontent.com/68164552/126549969-5743f077-e9f2-4da5-bf22-d26cd650de93.png)

![image](https://user-images.githubusercontent.com/68164552/126550028-25a60378-704f-45f8-a273-48d5dabca420.png)

Agora o usuário precisa aparecer no Keycloak, retornamos no Keycloak em user federation clicamos em LDAP, e clicamos em "Syncronize changed users"

![image](https://user-images.githubusercontent.com/68164552/126550558-5d2cffd6-c85c-42d1-bf04-ee8c5f14455b.png)
 
 E verificamos o usuário Leonardo cadastrado no keycloak.
 
 ![image](https://user-images.githubusercontent.com/68164552/126550692-8973e97b-971e-4a4a-bb5b-40098e445cc1.png)

Pronto! Tudo ok.
