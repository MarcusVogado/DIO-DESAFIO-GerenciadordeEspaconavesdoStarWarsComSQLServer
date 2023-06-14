# DIO-DESAFIO-GerenciadordeEspaconavesdoStarWarsComSQLServer
Scripts para criação do banco de dados no SQLServer
</br>
<h1>Para a criação do banco de dados execute as seguintes Querys:</h1></br>
</br>
<h1><b>TABELA PLANETAS</b></h1></br>
CREATE TABLE Planetas(</br>
</br>
IdPlaneta int NOT NULL,</br>
Nome varchar (50) NOT NULL,</br>
Rotacao float NOT NULL,</br>
Orbita float NOT NULL,</br>
Diametro float NOT NULL,</br>
Clima varchar(50)NOT NULL,</br>
Populacao int NOT NULL</br>
)</br>
GO </br>
ALTER TABLE Planetas ADD CONSTRAINT Pk_Planetas PRIMARY KEY (IdPlaneta);</br>
GO</br>
<h1><b>TABELA NAVES</b></h1></br>
</br>
CREATE TABLE Naves(</br>

IdNave int NOT NULL,</br>
Nome varchar(100) NOT NULL,</br>
Modelo varchar(150) NOT NULL,</br>
Passageiros int NOT NULL,</br>
Carga float NOT NULL,</br>
Classe varchar(100)NOT NULL</br>
)</br>
ALTER TABLE Naves ADD CONSTRAINT Pk_Naves PRIMARY KEY (IdNave);</br>
GO</br>

<h1><b>TABELA PILOTOS</b></h1></br>
</br>

CREATE TABLE Pilotos(</br>
IdPiloto int NOT NULL,</br>
Nome varchar(200) NOT NULL,</br>
AnoNascimento varchar(10) NOT NULL,</br>
IdPlaneta int NOT NULL</br>
)</br>
GO</br>
ALTER TABLE Pilotos ADD CONSTRAINT Pk_Pilotos PRIMARY KEY (IdPiloto);</br>
GO</br>
ALTER TABLE Pilotos ADD CONSTRAINT FK_Pilotos_Planetas FOREIGN KEY(IdPlaneta)</br>
REFERENCES Planetas(IdPlaneta);</br>

GO</br>
<h1><b>TABELA PILOSTONAVES</b></h1></br>
</br>

CREATE TABLE PilotosNaves(</br>
FlagAutorizado bit NOT NULL,</br>
IdPiloto int NOT NULL,</br>
IdNave int NOT NULL</br>
)</br>
GO</br>
ALTER TABLE PilotosNaves ADD CONSTRAINT Pk_PilotosNaves PRIMARY KEY (IdPiloto, IdNave);</br>
GO</br>
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Pilotos FOREIGN KEY(IdPiloto)</br>
REFERENCES Pilotos(IdPiloto);</br>
GO</br>
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Naves FOREIGN KEY(IdNave)</br>
REFERENCES Naves(IdNave);</br>
GO</br>
ALTER TABLE PilotosNaves ADD CONSTRAINT DF_PilotosNaves_FlagAutorizado DEFAULT (1) FOR FlagAutorizado;</br>
GO</br>
<h1><b>TABELA HISTORICOVIAGENS</b></h1></br>
</br>
CREATE TABLE HistoricoViagens(</br>
IdNave int NOT NULL,</br>
IdPiloto int NOT NULL,</br>
DtSaida datetime NOT NULL,</br>
DtChegada datetime NULL</br>
)</br>
GO</br>
ALTER TABLE HistoricoViagens ADD CONSTRAINT FK_HistoricoViagens_PilotosNaves FOREIGN KEY (IdPiloto,IdNave)</br>
REFERENCES PilotosNaves (IdPiloto,IdNave);</br>
GO</br>
ALTER TABLE HistoricoViagens CHECK CONSTRAINT FK_HistoricoViagens_PilotosNaves;</br>


--Aluno Dio.ME Marcus vogado </br>
