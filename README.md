# supermaia_bd_projeto

create database SuperMaia
character set utf8mb4

collate utf8mb4_unicode_ci;

use SuperMaia;

create table Estoque(
id_estoque int auto_increment primary key,
nome_produto varchar(100) not null,
quantidade int not null,
preco decimal(10, 2) not null,
data_entrada date not null,
caract_produto text
);

create table Funcionarios (
id_funcionario int auto_increment primary key,
nome_funcionario varchar(100) not null,
telefone varchar(15),
email varchar(100),
cargo varchar(50),
salario decimal(10,2),
data_contratacao date not null
);

create table Vendas(
id_venda int auto_increment primary key,
data_venda date not null,
total decimal(10,2) not null,
id_cliente int not null,
id_funcionario int not null
);


create table Itens_Venda(
id_item_venda int auto_increment primary key,
id_venda int,
id_estoque int,
quantidade_vendida int not null,
preco_unitario decimal(10,2) not null,
constraint fk_itens_venda_venda foreign key (id_venda) references Vendas(id_venda),
constraint fk_itens_venda_estoque foreign key (id_estoque) references Estoque(id_estoque)
);

alter table Vendas
    add index idx_id_funcionario (id_funcionario),
add constraint fk_vendas_funcionario foreign key (id_funcionario) references Funcionarios(id_funcionario);

INSERT INTO estoque (nome_produto, quantidade, preco, data_entrada, caract_produto) values
('arroz','500','50.00','2024-05-03','pacote de 3kg de arroz'),
('feijao','452','23.00','2024-05-24','pacote de 1kg de feijao'),
('brinquedos','150','25.00','2024-05-18','Brinquedo interativo para criancas'),
('racao de cachorrro','75','70.00','2024-05-20','racao para caes'),
('shampoo','200','30.00','2024-01-20','Shampoo antcaspa 20g'),
('macarrao','145','09.00','2024-05-22','macarrao palito 30g'),
('paes','75','10.00','2024-05-25','paes 1kg: 10,00'),
('miojo','100','03.50','2024-05-27','miojo 15g'),
('nascau','90','12.00','2024-05-30','chocolate em po 20g'),
('leite 1L','40','08.00','2024-05-02','leite 1L'),
('chocolate nestle','35','80.00','2024-05-05','chocolate nestle meio amargo'),
('tomate','500','12.00','2024-05-07','tomate 12,00 1kg, tomate 00,25 a unid.');

insert into funcionarios (nome_funcionario, telefone, email, cargo, salario, data_contratacao) values
('Ava Gina', '11900000001', 'avagina@gmail.com', 'repositor', 1400.00, '2024-04-01'),
('Decio Pinto', '11900000002', 'DP@gmail.com', 'caixa', 1700.00, '2024-04-02'),
('Paula Tejando', '11900000003', 'PaulaVadinho@gmail.com', 'repositor', 1400.00, '2024-04-03'),
('Chuck Norris', '11900000004', 'CNORRIS@gmail.com', 'repositor', 1400.00, '2024-04-04'),
('Rambo', '11900000005', 'marcelo@gmail.com', 'repositor', 1400.00, '2024-04-05'),
('Xuxa', '11900000006', 'carlinhos@gmail.com', 'estoquista', 1600.00, '2024-04-06'),
('Ayrton Senna', '11900000007', 'curvafechada@gmail.com', 'caixa', 1700.00, '2024-04-07'),
('Fiat uno', '11900000008', 'patriciabravanel@gmail.com', 'caixa', 1700.00, '2024-04-08'),
('Daniel Pennis', '11900000009', 'danni@gmail.com', 'servicos gerais', 1200.00, '2024-04-09'),
('Sr. Respect', '11900000010', 'claudio@gmail.com', 'Gerente', 2100.00, '2024-04-10'),
('Osama Bin Laden', '11900000011', 'laden@gmail.com', 'estoquista', 2200.00, '2024-04-11'),
('Socrates', '11900000012', 'plataoserieB@gmail.com', 'servicos gerais', 1200.00, '2024-04-12'),
('Kadu Kando', '11900000013', 'gustavo@gmail.com', 'estoquista', 1600.00, '2024-04-13'),
('Zeca P. Gordinho', '11900000014', 'eduardo@gmail.com', 'padeiro', 1575.00, '2024-04-14'),
('Julia Mello Pinto', '11900000015', 'julia@gmail.com', 'Recepcionista', 1452.00, '2024-04-15');
