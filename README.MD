-- Exercicios BD PROA 
SELECT * FROM filmes;

-- Quantas vezes Natalie Portman foi indicada ao Oscar?
SELECT * FROM filmes WHERE nome_do_indicado="Natalie Portman";

-- Quantos Oscars Natalie Portman ganhou?
SELECT COUNT(*) FROM filmes WHERE nome_do_indicado="Natalie Portman" AND vencedor = "Sim";

-- Amy Adams já ganhou algum Oscar?
SELECT * FROM filmes WHERE nome_do_indicado= "Amy Adams" AND vencedor = "Sim";

-- A série de filmes Toy Story ganhou um Oscar em quais anos?
SELECT ano_cerimonia,categoria FROM filmes WHERE nome_filme LIKE "Toy Story%" AND vencedor = "Sim";

-- A partir de que ano que a categoria "Actress" deixa de existir? 
SELECT MAX(ano_cerimonia) FROM filmes WHERE categoria ="ACTRESS" ;

-- O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
SELECT nome_do_indicado, ano_cerimonia FROM filmes WHERE categoria = 'ACTRESS' AND  vencedor = 'Sim' ORDER BY ano_cerimonia LIMIT 1;

-- 7 Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0. 
UPDATE filmes
SET vencedor = CASE 
    WHEN vencedor = 'Sim' THEN 1
    WHEN vencedor = 'Não' THEN 0
    ELSE vencedor
END;

-- 8 Em qual edição do Oscar "Crash" concorreu ao Oscar?
SELECT  DISTINCT edicao_cerimonia FROM filmes WHERE nome_filme = "Crash";

 
-- 9 Bom... dê um Oscar para um filme que merece muito, mas não ganhou.
DELETE FROM filmes WHERE id_registro ="5586";
INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1977', '1978', '50', 'BEST PICTURE', 'Gary Kurtz, Producer', 'Star Wars', 'Sim');
SELECT * FROM filmes WHERE nome_filme='Star Wars';

-- 10 O filme Central do Brasil aparece no Oscar?
SELECT * FROM filmes WHERE nome_filme LIKE '%Central do Brasil%';
 
-- 11 Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. 
INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1978','1978','51','BEST PICTURE', 'John De Bello , Producer','Attack of the Killer Tomatoes','Não');
INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1988','1988','61','BEST PICTURE', 'John De Bello , Producer','Return of the Killer Tomatoes','Não');
INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('2016','2016','88','BEST PICTURE', 'Rafael Diaz Wagner , Producer','Attack of the Killer Donuts','Não');
 
-- 14 Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor? AND categoria = 'DIRECTING' AND vencedor = 'Sim' ;
SELECT nome_do_indicado, categoria FROM filmes WHERE ano_cerimonia= '2003' 
AND (categoria = 'BEST PICTURE' OR categoria = 'ACTRESS IN A LEADING ROLE' OR categoria = 'DIRECTING')
AND vencedor = 'Sim';