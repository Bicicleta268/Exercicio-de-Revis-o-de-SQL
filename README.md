CREATE DATABASE 3DSNOVOTECBD;
USE 3DSNOVOTECBD;

CREATE TABLE cliente (
    cpf INT(11) PRIMARY KEY NOT NULL,
    nome VARCHAR(50) NOT NULL,
    endereco VARCHAR(100) NOT NULL,
    cidade VARCHAR(20),
    telefone NUMERIC(11) NOT NULL,
);

CREATE TABLE carro (
    id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    placa INT (8) NOT NULL,
    cor VARCHAR(20) NOT NULL,
    modelo VARCHAR(20) NOT NULL,
    ano DATA NOT NULL,
    cpf_cliente NUMERIC(11),
    CONSTRAINT fk_cpf_cliente
	FOREIGN KEY (cpf_cliente)
    REFERENCES cliente (cpf)
);

CREATE TABLE manutencao (
    id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    data_manutencao DATE NOT NULL,
    valor FLOAT(8,2) NOT NULL,
    id_carro INTEGER,
    CONSTRAINT fk_id_carro
	FOREIGN KEY (id_carro)
    REFERENCES carro (id)
);
 
INSERT INTO cliente (cpf, nome, endereco, cidade, telefone) 
	VALUES (12345678901, "Solange Almeida", "R. 7 de setembro, 100", "", "15999999999"),
		   (98765432123, "Taís Araújo", "R. 31 de março, 400", "Votorantim", "15999999991"),
           (22233344455, "Marcos Palmeira", "R. Itavuvu, 1000", "", "15999999992"),
           (12312312312, "Junior Moraes", "R. Avarenga Dantas, 1", "Mairinque", "11999999993"),
           (44455566677, "Cristiane Torloni", "R. Marcio de Sá, 2", "São Roque", "15999999994"),
           (88877766655, "Maria do Bairro", "R. Ubirajara, 2", "", "15999999995");
           
SELECT * FROM cliente;

INSERT INTO carro (placa, cor, modelo, ano, cpf_cliente) 
	VALUES ("ABC1010", "Branca", "Corsa", 2007, 12345678901),
		   ("ABY1111", "Preta", "Uno", 2018, 98765432123),
		   ("VBN6543", "Prata", "Ka", 1900, 22233344455),
		   ("XAQ123", "Azul", "Corola", 1900, 12312312312),
		   ("XZA222", "Marrom", "Corola", 2001, 88877766655),
		   ("OPK8765", "Branca", "Gol ", 2010, 88877766655),
		   ("PPP3434", "Amarelo", "Palio", 2010, 44455566677),
		   ("BBB4561", "Prata", "Civic", 2017, 44455566677),
		   ("XXC1111", "Prata", "Civic", 2016, 12345678901);
	 
SELECT * FROM carro;

INSERT INTO manutencao (data_manutencao, id_carro, valor) 
	VALUES ("2018-09-24", 1, 800.00),
           ("2018-09-20", 2, 1000.00),
           ("2018-08-24", 1, 300.00),
           ("2018-08-24", 3, 450.00),
           ("2018-08-24", 4, 986.00),
           ("2018-07-24", 5, 555.00),
           ("2018-07-24", 6, 130.00),
           ("2018-05-01", 7, 1000.00),
           ("2018-05-01", 8, 1205.00);
	 
SELECT * FROM manutencao;

UPDATE cliente
    SET cidade = "Sorocaba"
    WHERE cidade = "";

SELECT * FROM cliente;

UPDATE carro
    SET modelo = 'Corolla'
    WHERE modelo = 'Corola';

SELECT * FROM carro;

UPDATE manutencao
    SET data_manutencao = "2018-01-01"
    WHERE valor > 1000.00;

SELECT * FROM manutencao;

DELETE FROM cliente WHERE nome = "Taís Araújo";
