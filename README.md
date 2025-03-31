# Tutorial SQLFLUFF
O SQLFluff é uma ferramenta open-source para análise estática de código SQL, que funciona como um linter e formatter. Ele ajuda a manter o código SQL padronizado, organizado e livre de erros de sintaxe e estilo.

## Instalação
Para instalar o SQLFluff, é necessário ter o [Python](https://www.python.org/downloads/) instalado.
1. Use o seguinte comando para instalação via pip:
  ```shell
  pip install sqlfluff
  ```
2. Verifique se a instalação foi bem sucedida:
  ```shell
  sqlfluff --version
  ```

## Configurações
Você pode criar um arquivo de configuração .sqlfluff no diretório raiz do seu projeto para definir regras específicas. 
1. Exemplo de um arquivo .sqlfluff configurando o dialeto para SQLite e algumas regras:

```sqlfluff
[sqlfluff]
dialect = sqlite
exclude_rules = L001,L002
```

## Uso
Você pode utilizar o linter tanto pelo terminal quanto por meio da extensão do VS Code.


1. Extensão do VS Code
Baixar a extensão [SQLFUFF](https://marketplace.visualstudio.com/items?itemName=dorzey.vscode-sqlfluff). Os problemas dos códigos SQL já aparecerá na saída do terminal, e para arrumá-los automaticamente, pressione F1 e selecione a opção "SQLFLUFF Fix".

2. Terminal:
  Usando o shell, é possível ver os problemas de um arquivo passando o nome no comando:
  ```shell
  sqlfluff lint meusql.sql
  ```
  Saída:
  ```output
  == [meusql.sql] FAIL
  L:   1 | P:   1 | LT09 | Select targets should be on a new line unless there is
                         | only one select target. [layout.select_targets]                                                
  L:   1 | P:  19 | CP01 | Keywords must be consistently upper case.
                         | [capitalisation.keywords]
  L:   1 | P:  30 | LT14 | The 'WHERE' keyword should always start a new line.
                         | [layout.keyword_newline]
  L:   1 | P:  49 | LT14 | The 'ORDER' keyword should always start a new line.
                         | [layout.keyword_newline]
  L:   1 | P:  56 | CP01 | Keywords must be consistently upper case.
                         | [capitalisation.keywords]
  L:   1 | P:  61 | LT12 | Files must end with a single trailing newline.
                         | [layout.end_of_file]
  ```

  Para arrumar os erros automaticamente, executar o seguinte comando:
  ```shell
  sqlfluff fix meusql.sql
  ```
