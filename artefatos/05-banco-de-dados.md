# Banco de Dados 
## Modelo Lógico do Banco de Dados
👀🎯 Em andamento <br>
![Screenshoot](/artefatos/imagens/data_model2.png)

## Script SQL criação das tabelas no banco 

```sql
-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema separai
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `separai` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci ;
USE `separai` ;

-- -----------------------------------------------------
-- Table `separai`.`enderecos`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`enderecos` (
  `id_endereco` INT NOT NULL AUTO_INCREMENT,
  `rua` VARCHAR(255) NOT NULL,
  `numero` INT NOT NULL,
  `bairro` VARCHAR(255) NOT NULL,
  `cidade` VARCHAR(255) NOT NULL,
  `estado` VARCHAR(255) NOT NULL,
  `uf` VARCHAR(2) NOT NULL,
  PRIMARY KEY (`id_endereco`))
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `separai`.`consumidores`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`consumidores` (
  `id_usuario` INT NOT NULL AUTO_INCREMENT,
  `enderecos_id_endereco` INT NOT NULL,
  `saldo_atual` DOUBLE NOT NULL,
  PRIMARY KEY (`id_usuario`, `enderecos_id_endereco`),
  INDEX `fk_consumidores_enderecos_idx` (`enderecos_id_endereco` ASC) VISIBLE)
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `separai`.`aparelhos`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`aparelhos` (
  `id_aparelho` INT NOT NULL AUTO_INCREMENT,
  `consumidores_id_usuario` INT NOT NULL,
  `tipo_aparelho` VARCHAR(255) NULL DEFAULT NULL,
  `funcionando` INT NOT NULL,
  PRIMARY KEY (`id_aparelho`, `consumidores_id_usuario`),
  INDEX `fk_aparelhos_consumidores1_idx` (`consumidores_id_usuario` ASC) VISIBLE)
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `separai`.`auth`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`auth` (
  `id_usuario` INT NOT NULL AUTO_INCREMENT,
  `consumidores_id_usuario` INT NOT NULL,
  `email` VARCHAR(255) NOT NULL,
  `nome_completo` VARCHAR(255) NULL DEFAULT NULL,
  `cpf` VARCHAR(11) NOT NULL,
  `senha` VARCHAR(60) NOT NULL,
  `tipo_usuario` INT NOT NULL,
  PRIMARY KEY (`id_usuario`, `consumidores_id_usuario`),
  INDEX `fk_auth_consumidores1_idx` (`consumidores_id_usuario` ASC) VISIBLE)
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `separai`.`pedidos`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`pedidos` (
  `id_pedido` INT NOT NULL AUTO_INCREMENT,
  `consumidores_id_usuario` INT NOT NULL,
  `status_pedido` INT NULL DEFAULT 0,
  `detalhes` VARCHAR(255) NULL DEFAULT NULL,
  `data_solicitacao` DATETIME NOT NULL,
  `data_aprovacao` DATETIME NULL DEFAULT NULL,
  `qtd_moedinhas` INT NULL,
  PRIMARY KEY (`id_pedido`, `consumidores_id_usuario`),
  INDEX `fk_pedidos_consumidores1_idx` (`consumidores_id_usuario` ASC) VISIBLE)
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `separai`.`pt_coleta`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `separai`.`pt_coleta` (
  `id_pt_coleta` INT NOT NULL AUTO_INCREMENT,
  `enderecos_id_endereco` INT NOT NULL,
  `CNPJ` VARCHAR(14) NOT NULL,
  `nome` VARCHAR(255) NOT NULL,
  PRIMARY KEY (`id_pt_coleta`, `enderecos_id_endereco`),
  INDEX `fk_pt_coleta_enderecos1_idx` (`enderecos_id_endereco` ASC) VISIBLE)
ENGINE = MyISAM
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
```
