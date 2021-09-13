# Controle de clientes, produtos e vendas

Este é um exercício de programação orientada a objeto utilizando PHP para desenvolver um simples sistema em terminal de controle de vendas.

### A. O ambiente

Crie a seguinte estrutura de projeto (sugestão):

```
/controle-vendas (pasta raiz)
├── /database (pasta com os arquivos de dados)
│     └── .gitkeep (arquivo que instrui ao git manter a pasta mesmo vazia)
├── /src (pasta com os arquivos fonte)
│     ├── /Models (pasta de entidades)
│     │     └── .gitkeep 
│     ├── /Controllers (pasta de controladores)
│     │     └── .gitkeep 
│     └── App.php (classe principal da aplicação)
├── /.gitignore (arquivo para identificar os diretórios e arquvios que serão ignorados pelo git)
├── /composer.json (arquivo de configuração do composer - criado automaticamente)
└── /index.php (arquivo ponto de entrada)
```

Outras pastas e arquivos serão criados automaticamente confirme comandos a serem executados.

### B. Configuração inicial do projeto

Configure o arquivo `.gitignore` com o seguinte conteúdo:

```
/vendor
/database/*.*
``` 

A linha acima indica que qualquer arquivo dentro da pasta `database` e a pasta `vendor` (que será criada pelo composer) será ignorado pelo git. 
Caso esteja usando a IDE phpStorm adicione a linha `/.idea` ao arquivo tambem.

Crie o arquivo de configuração do composer:

```
composer init
```

O comando acima vai criar o arquivo `composer.json` na raiz do projeto. Confirme as perguntas apertando ENTER e ao finalizar abra o arquivo e ele
deve conter o conteúdo parecido abaixo:

```
{
    "name": "nome/projeto",
    "authors": [
        {
            "name": "<teu nome aqui>",
            "email": "<teu email aqui>"
        }
    ],
    "require": {},
}
```

Agora ao final do bloco `"require": {},` vamos adicionar um novo bloco:

```
    "autoload": {
        "psr-4": {
            "App\\": "src/",
        }
    }
```

O resultado final do `composer.json` deve ser algo como esse:

```
{
    "name": "nome/projeto",
    "authors": [
        {
            "name": "<teu nome aqui>",
            "email": "<teu email aqui>"
        }
    ],
    "require": {},
    "autoload": {
        "psr-4": {
            "App\\": "src/",
        }
    }
}
```

O que acabamos de fazer foi configurar o **autoload** do composer, para que as classes e demais arquivos php possam ser adicionados automaticamente a cada
dependência que fomos adicionando. É algo parecido aos **import** do JAVA. Veremos isso mais adiante.

Configuramos para o PHP entender que o nosso `namespace` está em `App` que corresponde a pasta `src` logo todas as classes dentro desta pasta vão pertencer
ao **namespace** `App`.

Uma vez o arquivo `composer.json` estando configurado basta rodar o comando `composer dumpautoload` no terminal/prompt na pasta raiz para que a pasta `vendor` seja
criada junto com alguns arquivos dentro dela, dentre eles o arquivo `autoload.php` (que usaremos logo mais).

### C. O ponto de entrada 

Agora vamos configurar o ponto de entrada da aplicação no arquivo `index.php`:

```php
<?php

// carregamos o arquivo gerado pelo composer para que as classes sejam identificadas quando usadas
// isso evita a necessidade de ficar usando require para importar as classes dentro de outras classes
require_once("vendor/autoload.php"); 

use App; // instruímos o PHP para ler o namespace App

App::start(); // chamamos o método estático start da classe App.php

```

### D. A estrutura da aplicação

Atá agora fizemos apenas a configuração da estrutura do projeto, definimos a organização de algumas pastas e configuramos nosso arquivo `index.php` para 
chamar o método `start` da classe App.

A aplicação vai rodar no terminal, vai apresentar um menu de opções ao usuário para selecionar as seguintes opções:

- CLIENTES
- PRODUTOS
- VENDAS
- SAIR DO SISTEMA

A forma de seleção de opção se dá com o usuário digitando a opção que deseja. EX: `1 - CLIENTES`

Deve-se tambem ter uma opção para que o usuário saia da aplicação.

### D-1. Estrutura de menus

Menu inicial:

```
--------------------------------
 <MENSAGEM DE BOAS VINDAS>
 <TITULO DA APLICAÇÃO>
--------------------------------
1 - CLIENTES
2 - PRODUTOS
3 - VENDAS
Q - SAIR DO SISTEMA

Selecione a opção desejada: 
```

Menu clientes:

```
--------------------------------
 <TITULO DA APLICAÇÃO>
 CADASTRO DE CLIENTES
--------------------------------
1 - Listar clientes
2 - Adicionar um cliente
3 - Editar um cliente
4 - Excluir um cliente
S - Voltar ao menu inicial

Selecione a opção desejada: 
```

Menu Produtos:

```
--------------------------------
 <TITULO DA APLICAÇÃO>
 CADASTRO DE PRODUTOS
--------------------------------
1 - Listar produtos
2 - Adicionar um produto
3 - Editar um produto
4 - Excluir um produto
S - Voltar ao menu inicial

Selecione a opção desejada: 
```

... mais

Documento incompleto... 
