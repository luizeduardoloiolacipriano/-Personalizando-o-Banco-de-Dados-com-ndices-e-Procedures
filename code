create database if not exists company_db;
USE company_db;

create table departamento (
    id int auto_increment primary key,
    nome varchar(100),
    cidade varchar(100)
);

create table empregado (
    id int auto_increment primary key,
    nome varchar(100),
    salario decimal(10,2),
    departamento_id int,
    foreign key (departamento_id) references departamento(id)
);

--dados

insert into departamento (nome, cidade)
values
('TI', 'São paulo'),
('RH', 'Rio de janeiro'),
('marketing', 'Curitiba'),
('Financeiro', 'São paulo');

insert into empregado (nome, salario, departamento_id) 
values
('Luiz', 3000, 1),
('Gabriel', 4000, 1),
('joão', 2500, 2),
('Maria', 3500, 3),
('Lucas', 1000, 4);

--Departamento com maior numero de pessoas

select d.nome, count(e.id) as
total_funcionarios
from departamento d
join empregado e on e.departamento_id = d.id
group by d.id, d.nome
order by total_funcionarios desc
limit 1;

--Departamento por cidade

select cidade, nome
from departamento
order by cidade;

-- empregos por departamento
select d.nome as departamento, e.nome as empregado
from empregado e
join departamento d on e.departamento_id = d.id
order by d.nome;

--indices

-- join
create index idx_empregado_departameto on empregado(departamento_id);

--indice para chave
create index idx_departamento_id on departamento(id);

--indice buscar por cidade
create index idx_departamento_cidade on departamento(cidade);


create table universidade (
    id int auto_increment primary key
    nome varchar(100)
    cidade varchar(100)
);

create table produto (
    id int auto_increment primary key
    nome varchar(100)
    preco decimal (10,2)
);


-- procedure universidade 

demiter //
create procedure crud_universidade (
    in opcao int,
    in p_id int,
    in p_nome varchar(100),
    in p_cidade varchar(100)
)
begin
    
    If opcao = 1 then
       select * from universidade;
       
    elseif opcao = 2 then
        insert into universidade (nome, cidade)
        values (p_nome, p_cidade);
        
    elseif opcao 3 = then
        update universidade
        set nome = p_nome, cidade  = p_cidade
        where id = p_id;
        
    elseif opcao 4 then then
        delete from universidade
        where id = p_id;
    
    end If
        
end //
demiter ;

-- procedure  produto

delimiter //
create procedure crud_produto (
     in opcao int,
     in p_id int,
     in p_nome varchar(100),
     in p_preco decimal(10,2)
)
begin

     If opcao = 1 then
        select * from produto;
        
    elseif opcao = 2 then
        insert into produto (nome, preco)
        values (p_nome, p_preco);
        
    elseif opcao = 3 then
        update produto
        set nome  = p_nome, preco = p_preco
        where id = p_id;
        
    elseif opcao = 4 then
        delete from produto
        where id = p_id;
    
    end if;
    
end //

delimiter;

--teste prodedures

call crud_universidade(2, null, 'usp', "São paulo");
call crud_universidade(2, null, 'Unesp', 'Presidente  prudente');
call crud_universidade(1, null, null, null, null);
call crud_universidade(3, 1, 'USP atualizada', 'SP');
call crud_universidade (4, 2, null, null);


-- produto
call crud_produto(2, null, 'notebook', 3500.00);
call crud_produto(2, null, 'Mouse', 100.00);
call crud_produto(1, null, null, null);
call crud_produto(3, 1, 'computador', 5000.00);
call crud_produto(4, 2, null, null);
