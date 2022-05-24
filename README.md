# Modelagem de banco de dados e execução em docker

Atividade proposta durante a participação na trilha de Engenharia de Dados do Programa de Formação em Dados Encantech, realizado durante os meses de Março, Abril e Maio de 2022, em uma parceria entre as Lojas Renner S.A. e a CESAR School. 

Consiste na modelagem de um banco de dados, da criação de um gerador de massa e da execução em um docker.


## Mini mundo

Uma faculdade contratou você como engenheiro de dados e pediu seu apoio para a construção de um modelo de banco de dados para gerenciar seus funcionários, divididos entre administrativos e professores, permitindo também alocar um professor por matéria por semestre, permitindo assim a rotação entre os professores durante os semestres.

O sistema também deve registrar os dados de matrícula dos alunos, o ano letivo e suas matérias que serão cursadas por semestre, vinculando aos professores que irão ministrar aulas nesse período.

Os dados referentes aos alunos devem conter sua filiação, sua data de nascimento, endereço completo, telefone para contato, e-mail e seu histórico de notas por matérias.


## Modelagem

[Modelos conceitual e lógico](https://github.com/peuvitor/modelagem-banco-de-dados-e-docker/tree/main/modelagem-banco-de-dados)

[Modelo físico](https://github.com/peuvitor/modelagem-banco-de-dados-e-docker/blob/main/scripts_sql/DDL_FACULDADE.sql): gerado a partir do MySQL Workbench.


## Gerador de massa

Arquivos de suporte: lista de nomes, lista de sobrenomes e lista de CEPs válidos.

Gerado script que popula a base de dados na seguinte ordem:

1. tabelas de domínio (exemplos: CIDADE, DEPARTAMENTO);

2. tabelas que dependem apenas das tabelas de domínio (exemplo: PESSOA);

3. tabelas de especializações (exemplos: ALUNO, PROFESSOR);

4. tabelas de relacionamentos (exemplo: AULA).


## Docker

Criação de um docker a partir de uma imagem do SGBD MariaDB.

### Rodar os scripts SQL no docker criado

1. criar docker a partir do arquivo 'docker-compose.yml'

	docker-compose -f ./docker-compose.yml up -d

2. executar docker

	docker exec -i \<NOME-DO-DOCKER\> mysql -u root -p\<SENHA\> < \<NOME-DO-ARQUIVO\>.sql
