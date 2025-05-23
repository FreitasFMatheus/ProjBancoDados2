# Proj 2 Banco de Dados Steam Proj

## Integrantes do Grupo

* Matheus Ferreira de Freitas
  RA: 22.125.085.5
* Henrique Hodel Babler
  RA: 22.125.084.8

---

## Ordem de Execução

1. **CriarTabelas.py**
   Cria todas as tabelas do banco necessárias para o projeto.
   1.1. Se ocorrer algum erro nas tabelas, use **ApagarTudo.py** para reiniciar a estrutura do banco.
2. **PreencherBanco.py**
   Insere dados de exemplo em todas as tabelas para testes.
   2.1. Se precisar limpar apenas os dados sem alterar a estrutura, use **LimparBanco.py**.
3. **ValidarDados.py**
   Executa verificações básicas de contagem e integridade dos registros.

---

## Queries Interessantes

No arquivo `QuerriesInteressantes.txt` você encontra explicações detalhadas para cada query utilizada.

---

## Modelo Conceitual (Mermaid)

```mermaid
erDiagram
    DESENVOLVEDOR {
        int id_dev
        varchar nick
        int numerodejogos
    }
    PUBLICADORA {
        int id_pub
        varchar nome
    }
    JOGADOR {
        int id_jogador
        varchar nick
        int numerodejogos
    }
    JOGO {
        int id_jogo
        varchar titulo
        varchar tema
        int id_dev
    }
    PLATAFORMA {
        int id_plataforma
        varchar nome
        int porcentagem_plataforma
        numeric preco_publicacao
    }
    CONTRATO {
        int id_contrato
        date data_comeco
        date data_fim
        boolean terminou
        int porcentagem_publicadora
        int porcentagem_dev
        int id_jogo
        int id_pub
    }
    VENDA {
        int id_venda
        numeric preco
        int id_jogador
        int id_jogo
    }
    VENDA_CONTRATO {
        int porcentagem_contrato
        int id_contrato
        int id_venda
        int id_plataforma
    }

    DESENVOLVEDOR ||--o{ JOGO           : desenvolve
    JOGO        ||--o{ CONTRATO       : possui
    PUBLICADORA ||--o{ CONTRATO       : assina
    CONTRATO    ||--o{ VENDA_CONTRATO : gera
    PLATAFORMA  ||--o{ VENDA_CONTRATO : disponibiliza
    JOGO        ||--o{ VENDA          : vende
    JOGADOR     ||--o{ VENDA          : realiza
```
