# Banco de Dados 
## Modelo Lógico do Banco de Dados
👀🎯 Em andamento <br>
![Screenshoot](/artefatos/imagens/data_model.png)

## Script SQL criação das tabelas no banco 

```sql
CREATE DATABASE separai ;
USE separai;
CREATE TABLE auth (
	id_usuario int,
    email varchar(255),
    nome_completo varchar(255),
    cpf varchar(255),
    senha varchar(255),
    tipo_usuario varchar(255)
);

CREATE TABLE pedidos (
    id_pedido int,
    status_pedido varchar(255),
    id_usuario_solicitante varchar(255),
    id_pt_coleta varchar(255),
    aparelho varchar(255),
    detalhes varchar(255),
    data_solicitacao varchar(255),
    data_aprovacao varchar(255),
    qtd_moedinhas varchar(255)
);

CREATE TABLE consumidores (
    id_usuario int,
    id_endereco varchar(255),
    saldo_atual varchar(255)
    );

CREATE TABLE pt_coleta (
    id_pt_coleta int,
    CNPJ varchar(255),
    id_endereco varchar(255)
);

CREATE TABLE enderecos (
    id_endereco int,
    rua varchar(255),
    numero varchar(255),
    bairro varchar(255),
    cidade varchar(255),
    estado varchar(255)
);

CREATE TABLE aparelhos (
    id_aparelho int,
    tipo_aparelho varchar(255),
    funcionando  varchar(255),
    id_pt_coleta  varchar(255),
);
```