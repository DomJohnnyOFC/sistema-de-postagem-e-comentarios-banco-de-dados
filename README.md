
# Projeto de Banco de Dados (parte 2)

**Nome do Projeto:** Rede Social Conecta  
**Equipe de Desenvolvimento:** Dom Johnny Studios

## 1~Visão Geral do Sistema (Escopo)

A Rede Social Conecta tem como objetivo permitir que seus usuários possam criar uma conta, realizar postagens e interagir por meio de comentários. O sistema será responsável por armazenar e organizar as informações dos usuários, das postagens realizadas e dos comentários feitos nas publicações.

A plataforma permitirá que cada usuário tenha seu próprio cadastro e possa criar diversas postagens. Outros usuários poderão visualizar as publicações e realizar comentários, possibilitando uma interação simples entre os usuários da rede social.

## 2~Regras de Negócio

**RN01:** O sistema deve gerenciar o cadastro dos usuários. As informações necessárias para o cadastro são:

-   Nome completo
    
-   E-mail
    
-   Senha
    
-   Data de cadastro
    

**RN02:** O sistema deve permitir que os usuários criem postagens. As informações necessárias são:

-   Texto da postagem
    
-   Data e hora da publicação
    
-   Usuário responsável pela postagem
    

**RN03:** Cada postagem deve estar relacionada a apenas um usuário, sendo esse usuário identificado como o autor da publicação.

**RN04:** Um usuário poderá realizar várias postagens dentro do sistema.

**RN05:** O sistema deve permitir que os usuários realizem comentários nas postagens. As informações necessárias são:

-   Texto do comentário
    
-   Data e hora do comentário
    
-   Usuário responsável pelo comentário
    
-   Postagem comentada
    

**RN06:** Cada comentário deve estar relacionado a apenas um usuário e a uma postagem.

**RN07:** Um usuário poderá realizar vários comentários em diferentes postagens.

**RN08:** Uma postagem poderá receber vários comentários de diferentes usuários.

**RN09:** O sistema deve permitir que o usuário edite ou exclua suas próprias postagens.

**RN10:** O sistema deve permitir que o usuário edite ou exclua seus próprios comentários.

## 3~Requisitos Funcionais

**RF01:** O sistema deve permitir o cadastro de novos usuários.

**RF02:** O sistema deve permitir a alteração dos dados cadastrados pelo usuário.

**RF03:** O sistema deve permitir a exclusão de um usuário.

**RF04:** O sistema deve permitir a criação de novas postagens.

**RF05:** O sistema deve permitir a visualização das postagens cadastradas.

**RF06:** O sistema deve permitir a edição de uma postagem pelo seu autor.

**RF07:** O sistema deve permitir a exclusão de uma postagem pelo seu autor.

**RF08:** O sistema deve permitir que usuários comentem nas postagens.

**RF09:** O sistema deve permitir a visualização dos comentários de uma postagem.

**RF10:** O sistema deve permitir que o autor edite seu comentário.

**RF11:** O sistema deve permitir que o autor exclua seu comentário.

**RF12:** O sistema deve identificar o usuário responsável por cada postagem.

**RF13:** O sistema deve identificar o usuário responsável por cada comentário.

## 4~Entidades do Sistema

### Usuário

Responsável pelo cadastro e pelas interações realizadas na rede social.

**Atributos:**

-   ID do usuário
    
-   Nome completo
    
-   E-mail
    
-   Senha
    
-   Data de cadastro
    

### Postagem

Representa uma publicação realizada por um usuário.

**Atributos:**

-   ID da postagem
    
-   Texto
    
-   Data e hora
    
-   ID do usuário
    

### Comentário

Representa uma interação realizada por um usuário em uma postagem.

**Atributos:**

-   ID do comentário
    
-   Texto
    
-   Data e hora
    
-   ID do usuário
    
-   ID da postagem
    

## 5~Relacionamentos

**Usuário → Postagem**

Um usuário pode criar várias postagens, porém cada postagem pertence a apenas um usuário.

**Cardinalidade:** 1:N

**Usuário → Comentário**

Um usuário pode realizar vários comentários, porém cada comentário pertence a apenas um usuário.

**Cardinalidade:** 1:N

**Postagem → Comentário**

Uma postagem pode receber vários comentários, porém cada comentário pertence a apenas uma postagem.

**Cardinalidade:** 1:N

## 6~Modelo Conceitual

O modelo conceitual deverá ser desenvolvido utilizando o **BrModelo**, representando as entidades, seus atributos, relacionamentos e respectivas cardinalidades.

O modelo deverá conter as seguintes entidades principais:

**USUÁRIO**

↓

**POSTAGEM**

↓

**COMENTÁRIO**

Além disso, deverá representar os relacionamentos:

-   Usuário **cria** Postagem
    
-   Usuário **faz** Comentário
    
-   Postagem **recebe** Comentário

## Modelagem Conceitual
![](modelo-conceitual-v1.png)

## Modelagem Logica
![](modelo_logico.png)

# DOCUMENTO DE REQUISITOS — REDE SOCIAL

**Módulo: Postagens e Comentários**

## 1. OBJETIVO

O sistema deverá permitir que usuários cadastrados publiquem postagens e interajam por meio de comentários.

## 2. ENTIDADES PRINCIPAIS

* Usuário
* Postagem
* Comentário

## 3. REQUISITOS FUNCIONAIS

**RF01 — Cadastrar usuário**
O sistema deverá permitir o cadastro de usuários com nome completo, e-mail, senha e data de cadastro.

**RF02 — Identificar usuário**
Cada usuário deverá possuir um identificador único (`id_usuario`).

**RF03 — Criar postagem**
O sistema deverá permitir que um usuário cadastrado crie uma postagem informando o texto e a data/hora.

**RF04 — Relacionar postagem ao usuário**
Cada postagem deverá estar vinculada a um único usuário autor. Um usuário poderá criar várias postagens.

**RF05 — Criar comentário**
O sistema deverá permitir que um usuário cadastrado faça comentários em postagens.

**RF06 — Relacionar comentário à postagem**
Cada comentário deverá pertencer a uma única postagem. Uma postagem poderá receber vários comentários.

**RF07 — Relacionar comentário ao usuário**
Cada comentário deverá estar vinculado ao usuário que o realizou. Um usuário poderá realizar vários comentários.

**RF08 — Consultar postagens**
O sistema deverá permitir visualizar as postagens cadastradas e seus respectivos autores.

**RF09 — Consultar comentários**
O sistema deverá permitir visualizar os comentários associados a cada postagem e seus respectivos autores.

## 4. REQUISITOS DE DADOS

### Usuário

* `id_usuario`: chave primária
* `nome_completo`
* `email`
* `senha`
* `data_cadastro`

### Postagem

* `id_postagem`: chave primária
* `id_usuario`: chave estrangeira para Usuário
* `texto`
* `data_hora`

### Comentário

* `id_comentario`: chave primária
* `id_postagem`: chave estrangeira para Postagem
* `id_usuario`: chave estrangeira para Usuário
* `texto`
* `data_hora`

## 5. REGRAS DE NEGÓCIO

**RN01 — E-mail único**
O e-mail de cada usuário deverá ser único no sistema.

**RN02 — Autor da postagem**
Toda postagem deverá possuir um único usuário como autor.

**RN03 — Autor do comentário**
Todo comentário deverá possuir um único usuário como autor.

**RN04 — Postagem do comentário**
Todo comentário deverá estar associado a uma postagem existente.

**RN05 — Postagens por usuário**
Um usuário poderá criar várias postagens.

**RN06 — Comentários por postagem**
Uma postagem poderá receber vários comentários.

**RN07 — Comentários por usuário**
Um usuário poderá realizar vários comentários.

**RN08 — Integridade referencial**
A exclusão de registros deverá respeitar as regras de integridade referencial definidas no banco de dados.

## 6. RELACIONAMENTOS DO MODELO CONCEITUAL

* **Usuário (1) — (N) Postagem:** relacionamento **“cria”**.
* **Usuário (1) — (N) Comentário:** relacionamento **“faz”**.
* **Postagem (1) — (N) Comentário:** relacionamento **“recebe”**.

## 7. MODELO LÓGICO

### USUARIO

```text
USUARIO (
    id_usuario PK,
    nome_completo,
    email,
    senha,
    data_cadastro
)
```

### POSTAGEM

```text
POSTAGEM (
    id_postagem PK,
    id_usuario FK → USUARIO.id_usuario,
    texto,
    data_hora
)
```

### COMENTARIO

```text
COMENTARIO (
    id_comentario PK,
    id_postagem FK → POSTAGEM.id_postagem,
    id_usuario FK → USUARIO.id_usuario,
    texto,
    data_hora
)
```

