# 🛠️ Projeto Oficina Mecânica - Modelagem de Banco de Dados

Este projeto foi desenvolvido como parte do curso **"Construindo um esquema conceitual do zero"** da [Digital Innovation One](https://www.dio.me/). O objetivo é criar um esquema conceitual completo para um sistema de gerenciamento de oficina mecânica.

## 📋 Narrativa do Sistema

> Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica. Clientes levam veículos à oficina para consertos ou revisões periódicas. Cada veículo é designado a uma equipe de mecânicos que identifica os serviços necessários e preenche uma OS com data de entrega. O valor é calculado com base em tabelas de referência de mão-de-obra e peças utilizadas.

## 🔍 Entidades Principais

| Entidade           | Descrição                                  |
|--------------------|-------------------------------------------|
| `CLIENTE`          | Supertipo para clientes PF/PJ             |
| `CLIENTE_PF`       | Clientes pessoa física                    |
| `CLIENTE_PJ`       | Clientes pessoa jurídica                  |
| `VEICULO`          | Veículos dos clientes                     |
| `ORDEM_SERVICO`    | Ordens de serviço da oficina              |
| `SERVICO`          | Serviços oferecidos pela oficina          |
| `EQUIPE`           | Equipes de mecânicos                      |
| `MECANICO`         | Mecanicos da oficina                      |
| `PRODUTO_PECA`     | Peças/Produtos utilizados                 |
| `ESTOQUE`          | Controle de estoque de peças              |

## 🔗 Relacionamentos Chave

```mermaid
erDiagram
    CLIENTE ||--o{ VEICULO : possui
    CLIENTE {
        int idcliente PK
        enum tipo
    }
    CLIENTE_PF ||--o| CLIENTE : extends
    CLIENTE_PJ ||--o| CLIENTE : extends
    VEICULO ||--o{ ORDEM_SERVICO : tem
    ORDEM_SERVICO }|--|| EQUIPE : designada
    EQUIPE ||--o{ MECANICO : contem
    ORDEM_SERVICO }|--|{ SERVICO : inclui
    ORDEM_SERVICO }|--|{ PRODUTO_PECA : utiliza
    PRODUTO_PECA }|--|| ESTOQUE : tem


