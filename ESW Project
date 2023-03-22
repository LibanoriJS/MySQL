create database if not exists floricultura;
use floricultura;

create table if not exists fornecedor
( forCNPJ VARCHAR(18) not null,
  nome VARCHAR(99) not null,
  endereco VARCHAR(99) not null,
  telefone VARCHAR(99) not null, 
  primary key (forCNPJ));

create table if not exists produtos
(idProduto INT not null,
 preco DECIMAL(5,2) not null,
 qtdeMin INT not null,
 descricao VARCHAR(45) not null,
 tipo VARCHAR(45) not null,
 tamanho VARCHAR(12) not null,
 cor VARCHAR(45) not null,
 primary key(idProduto));

 create table if not exists pedidos
( idPedido INT  primary key not null,
  qtdePedido INT not null,
  dataPedido DATE not null,
  forCNPJ VARCHAR (18) not null,
  idProduto INT not null,
  foreign key (forCNPJ) references fornecedor (forCNPJ));
  
  create table if not exists recebidos
  (idEntrega INT primary key not null, 
   dataReceb DATE not null,
   qtdeRecebido INT not null,
   situacao VARCHAR(45) not null,
   idPedido INT not null,
   foreign key (idPedido) references pedidos (idPedido));
  
 ALTER TABLE fornecedor
 ADD Email varchar(99);
 
       
     INSERT INTO fornecedor VALUES
 (94206581000173, "Antônia e Kevin arranjos ME", "Praça Maestro Jorge Galatti", 1436615448,"contabilidade@antoniaekevincomerciome.com.br"),
 (59113717000192, 'Márcia e Rafael Entregas Expressas Ltda', 'Rua Aleixo Vaz da Costa',1126728325, 'seguranca@marciaerafaelentregasexpressasltda.com.br'),
 (91023142000120, 'Liz e Calebe Vasos ME', 'Parque Arariba',  1138146393, 'contabil@lizecalebevasosme.com.br'),
 (71103754000115, 'StellaFlores ME', "Rua José Gonçalves", 1935131336, 'vendas@stellaflores.com.br');
 
 INSERT INTO produtos VALUES
 (1, 3.50, 50, 'rosa','flor','P', 'vermelha' ),
 (2, 4.00, 20, "margarida",'flor', 'M', 'branca'),
 (3, 3.00, 20, 'tulipa','flor', 'P','azul'),
 (5, 4.00, 10, 'girassol', 'flor', 'G', 'amarelo'),
 (6, 3.70, 20, 'cartão', 'decoração', 'P', 'rosa'),
 (7, 6.00, 15, 'cesto', 'decoração', 'P', 'marrom'),
 (8, 10.00,40, 'vaso', 'recipiente', 'M','marsala'),
 (9, 8.00, 10, 'terra', 'saco','M', 'preta');
 
 INSERT INTO pedidos VALUES
 (001, 200, '2021-07-02', 71103754000115,4),
 (002, 150, '2021-11-03', 94206581000173, 3),
 (024,  100, '2020-12-16',94206581000173,1),
 (007, 300, '2021-08-23', 71103754000115,2);
 
 INSERT INTO recebidos VALUES
  (96, '2021-11-16', 150, 'completo', 002),
  (55, '2021-09-05', 150, 'parcial', 007),
  (23, '2020-12-30', 100, 'completo', 024),
  (56, '2021-07-20', 100, 'parcial', 001);
  
 
 select * from fornecedor;
 select * from produtos;
 select * from pedidos;
 select * from recebidos;
 
 
  INSERT INTO produtos VALUES 
 (10, 29.90, 10, 'adubo','fertilizante','m', 71103754000115),
 (11, 5.50, 20, "orquídea",'flor', 'm', 94206581000173),
 (12, 2.00, 10, "bico de papagaio",'flor', 'm', 91023142000120);
 
 
 #1 Nomes de fornecedor que comecam com A
 select * from fornecedor where nome like 'a%';
 
 #2 Media dos preços dos produtos
 select format(avg(preco),2) as 'Média de preços' from produtos;
 
 #3 Exibe produtos com o preço entre 4 e 20 Reais
 select * from produtos where preco >= 4 and preco <=20;

#4 Conta quantos produtos tem quantidade mínima maior ou igual a 20
select count(idProduto) as 'produtos' from produtos where qtdeMin >= 20;

#5 Exibe as relaçoes entre os fornecedores preços e produtos
Select pd.idPedido, pd.dataPedido, pd.idProduto,
                f.forCNPJ, f.nome
from pedidos pd join fornecedor f
on pd.forCNPJ = f.forCNPJ order by idPedido asc;

#6 Preço mínimo de cada produto em estoque
select idProduto , descricao, qtdeMin, preco, preco*qtdeMin as 'Valor mínimo em estoque' from produtos;

#7 Quantidade total de produtos a receber
select sum(qtdePedido) as 'Quantidade total de produtos a receber' from pedidos;

#8 Tamanhos de recipientes disponiveis
select tamanho as 'Tamanhos disponíveis' from produtos group by tamanho;

#9 Relaçao entre data de pedido e recebido
select pd.idPedido, pd.dataPedido,
 r.dataReceb
from pedidos pd inner join recebidos r
on pd.idPedido=r.idPedido order by (dataReceb);

#10 Relaçao entre pedidos e fornecedores, tal qual começa com a letra A
select 
pd.idPedido,
 f.nome
from pedidos pd inner join fornecedor f
on pd.forCNPJ=f.forCNPJ where nome like 'a%';

#11 Exibe prdutos de tamanho pequeno
select * from produtos where tamanho like 'p%';

#12 Exibe a relaçao entre a data do pedido e fornecedor, considerando apenas os produtos diversos
select pd.idPedido, pd.dataPedido, f.nome
from pedidos pd inner join fornecedor f
on pd.forCNPJ=f.forCNPJ where idPedido > 0;

#drop database floricultura
