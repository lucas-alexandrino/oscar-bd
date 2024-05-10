   <body>
   <h1>Exercícios BD PROA</h1>
    
        <strong>1. Listar todos os filmes:</strong></li>
        <p>SELECT * FROM filmes;</p>

        <strong>2. Quantas vezes Natalie Portman foi indicada ao Oscar?</strong></li>
        <p>SELECT * FROM filmes WHERE nome_do_indicado = "Natalie Portman";</p>

        <strong>3. Quantos Oscars Natalie Portman ganhou?</strong></li>
        <p>SELECT COUNT(*) FROM filmes WHERE nome_do_indicado = "Natalie Portman" AND vencedor = "Sim";</p>

        <strong>4. Amy Adams já ganhou algum Oscar?</strong></li>
        <p>SELECT * FROM filmes WHERE nome_do_indicado = "Amy Adams" AND vencedor = "Sim";</p>

        <strong>5. A série de filmes Toy Story ganhou um Oscar em quais anos?</strong></li>
        <p>SELECT ano_cerimonia, categoria FROM filmes WHERE nome_filme LIKE "Toy Story%" AND vencedor = "Sim";</p>

        <strong>6. A partir de que ano a categoria "Actress" deixa de existir?</strong></li>
        <p>SELECT MAX(ano_cerimonia) FROM filmes WHERE categoria = "ACTRESS";</p>

        <strong>7. O primeiro Oscar para melhor Atriz foi para quem? Em que ano?</strong></li>
        <p>SELECT nome_do_indicado, ano_cerimonia FROM filmes WHERE categoria = 'ACTRESS' AND vencedor = 'Sim' ORDER BY ano_cerimonia LIMIT 1;</p>

        <strong>8. Na coluna/campo "Vencedor", altere todos os valores "Sim" para 1 e todos os valores "Não" para 0.</strong></li>
        <p>UPDATE filmes
            SET vencedor = CASE
                WHEN vencedor = 'Sim' THEN 1
                WHEN vencedor = 'Não' THEN 0
                ELSE vencedor
            END;
        </p>

        <strong>9. Em qual edição do Oscar o filme "Crash" concorreu?</strong></li>
        <p>SELECT DISTINCT edicao_cerimonia FROM filmes WHERE nome_filme = "Crash";</p>

        <strong>10. Dê um Oscar para um filme que merece muito, mas não ganhou.</strong></li>
        <p>
            DELETE FROM filmes WHERE id_registro = "5586";<br>
            INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1977', '1978', '50', 'BEST PICTURE', 'Gary Kurtz, Producer', 'Star Wars', 'Sim');<br>
            SELECT * FROM filmes WHERE nome_filme='Star Wars';
        </p>

        <strong>11. O filme Central do Brasil aparece no Oscar?</strong></li>
        <p>SELECT * FROM filmes WHERE nome_filme LIKE '%Central do Brasil%';</p>

        <strong>12. Inclua no banco 3 filmes que nunca foram nomeados ao Oscar, mas que merecem ser.</strong></li>
        <p>
            INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1978','1978','51','BEST PICTURE', 'John De Bello , Producer','Attack of the Killer Tomatoes','Não');<br>
            INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('1988','1988','61','BEST PICTURE', 'John De Bello , Producer','Return of the Killer Tomatoes','Não');<br>
            INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor) VALUES ('2016','2016','88','BEST PICTURE', 'Rafael Diaz Wagner , Producer','Attack of the Killer Donuts','Não');
        </p>

        <strong>13. Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor no ano de 2003?</strong></li>
        <p>
            SELECT nome_do_indicado, categoria FROM filmes WHERE ano_cerimonia = '2003'
            AND (categoria = 'BEST PICTURE' OR categoria = 'ACTRESS IN A LEADING ROLE' OR categoria = 'DIRECTING')
            AND vencedor = 'Sim';
        </p>
    </ul>
    </body>