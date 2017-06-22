<html lang="pt-br">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=1024" />
    <meta name="apple-mobile-web-app-capable" content="yes" />
	<link href="http://fonts.googleapis.com/css?family=Open+Sans:regular,semibold,italic,italicsemibold|PT+Sans:400,700,400italic,700italic|PT+Serif:400,700,400italic,700italic" rel="stylesheet" />
    <link href="css/sql.css" rel="stylesheet" />    
    <link rel="shortcut icon" href="favicon.png" />
    <link rel="apple-touch-icon" href="apple-touch-icon.png" />

	<script type="text/javascript" src="js/shCore.js"></script>
	<script type="text/javascript" src="js/shBrushSql.js"></script>
	<link type="text/css" rel="stylesheet" href="css/shCoreDefault.css"/>
	<script type="text/javascript">SyntaxHighlighter.all();</script>

</head>

<body class="impress-not-supported">

	<div class="fallback-message">
		<p>Seu browser <b>não suporta os recursos</b> do impress.js, a apresentação será exibida de forma básica.</p>
		<p>Para melhor experiência use as últimas versões do <b>Chrome</b>, <b>Safari</b> ou <b>Firefox</b> browser.</p>
	</div>

	<div id="impress">
		
		<div class="step slide" data-x="0" data-y="0" data-z="0">
			<h1>SQL Server</h1>
			<q>O Microsoft SQL Server é um <b>SGBD</b><br />
			Sistema gerenciador de banco de dados relacional desenvolvido pela Microsoft.</q>
			<br /><br /><br />
			<b>* criado em 1988</b>
		</div>

		<div class="step" data-x="1000" data-y="1000" data-rotate-y="45">
			<h1>Objetivo</h1>
			<img width="900px" src="img/martelo.jpg">
		</div>	
		
		<div class="step slide" data-x="0" data-y="-1000" data-z="-100" data-z="0">
			<h1>Componentes</h1>
			&bull; Tabelas (entidades)<br/>			
			&bull; Registros (tuplas) - instância de uma tabela<br/>
			&bull; Colunas (atributos)<br/>
			&bull; Chaves (primária e estrangeira)<br/>			
			&bull; Relacionamentos<br/>
			&bull; Views<br/>
			&bull; Procedimentos e funções<br/>
			&bull; Triggers (gatilho)<br/>
			&bull; Índices<br/>
			&bull; Estatísticas<br/>
		</div>	
		
		<div class="step slide" data-x="2000" data-y="-1000" data-rotate-x="45">
			<h1>Índice</h1>
			<p>
				&bull; Estrutura em disco associado a uma tabela ou view<br/>
				&bull; Agiliza a recuperação das linhas<br/>
				&bull; Índices criados inadequadamente e a falta de índices são as principais fontes de afunilamentos<br/>
			</p>
			<q class="center">EXEMPLO - CEP</q>
			<img src="img/cep.jpg">
		</div>

		<div class="step slide" data-x="2000" data-y="-2000" data-rotate-x="90">
			<h1>B-Tree</h1>
			<q class="center">Como funciona?</q>
			<br/>
			<img src="img/b-tree.png">
		</div>

		<div class="step slide" data-x="3200" data-y="-2000" data-rotate-x="90">
			<q class="center">Intervalo</q>
			<br/>
			<img src="img/b-tree_2.png">
		</div>

		<div class="step slide" data-x="4400" data-y="-2000" data-rotate-x="90">
			<q class="center">Exemplo</q>
			<br/>
			<img src="img/b-tree_1.jpg">
		</div>

		<div class="step slide" data-x="5600" data-y="-2000" data-rotate-x="90">
			<q class="center">Curiosidades</q>
			<p>
				<br/>
				Consulta para <span class="texto-vermelho">50 linhas</span> <br/>
				em até <span class="texto-verde">6 passos</span>. <br/><br/>
				
				Consulta para mais de <span class="texto-vermelho">1 bilhão de linhas</span> <br/>
				em até <span class="texto-verde">30 passos</span>. <br/><br/>
				
				Complexidade <b>O(logN)</b> - 2^30 = 1.073.741.824 bilhão <br/><br/>
				
				Árvore Balanceada (folhas com profundidade aproximada) <br/> proporcional à altura da árvore.<br/><br/>
				
				<br/>
				<br/>
				<br/>
				<br/>
			</p>
			
		</div>		
		
		<div class="step slide" data-x="2000" data-y="-3000" data-rotate-x="135">
			<h1>Opções</h1>
			<q>ASC e DESC</q>
			<p>
				Praticamente indiferente em pesquisas<br/>
				Diferença em ordenação por mais de um campo
				</p>
			<q>Clustered e NonClustered</q>
			<p>
				Ordem de armazenamento em disco<br/>
				Vantagem pesquisa e desvantagem escrita<br/>
				PK é clustered - só é permitido um por tabela
			</p>
			<pre class="brush: sql;">
				create nonclustered index NomeIndice
				on Tabela (Campo1 asc, Campo2 desc);</pre>
		</div>

		<div class="step slide" data-x="2000" data-y="-4000" data-rotate-x="180">
			<h1>Quando</h1>
			<q>
				&bull; Campos de boa seletividade (5% - 10%)<br/>
				&bull; Evitar campos com muita alteração<br/>
				&bull; Criar índices em <b>FK</b><br/>
				&bull; Índice Composto > Vários Índices Simples<br/>
				&bull; Evitar Full Table Scan*<br/>
			</q>
		</div>

		<div class="step slide" data-x="2000" data-y="-5000" data-rotate-x="225">
			<h1>Composto</h1>
			<pre class="brush: sql;">
				select Nome, Sobrenome
				from   Clientes
				where  Nome = 'Chico'
				and    Sobrenome = 'Bento';</pre>
			<q>
				Criar um índice composto ( Nome, Sobrenome )
				é melhor que criar um índice para cada campo
			</q>
		</div>
		
		<div class="step slide" data-x="2000" data-y="-6000" data-rotate-x="225">
			<h1>Resumo</h1>
			<p>
				<span class="texto-verde">Vantagens</span><br/>
				&bull; Acesso aos dados reduzido<br/>
				&bull; Traz dados específicos de forma mais rápida<br/>
				&bull; Acesso de dados ordenados sem o custo da ordenação<br/>
				<br/>
				<span class="texto-vermelho">Desvantagens</span><br/>
				&bull; Piora performance em escritas (insert e update)<br/>
				&bull; Aumenta o consumo de memória e disco<br/>
				&bull; Necessidade maior de manutenção<br/>
				&bull; Pode diminuir a performance de consultas<br/>
				&nbsp;&nbsp;&nbsp; - Quando retornamos muitos dados da tabela<br/>
				&nbsp;&nbsp;&nbsp; - Quando volume de dados pequeno (adicionamos 1 etapa)<br/>
			</p>
		</div>
		
		<div class="step slide" data-x="2000">
			<h1>Escrevendo queries otimizadas</h1>
			<p>&bull;  Lógica de Conjuntos > Lógica de Procedimentos</p>
			<p>&bull;  Teste variações de queries objetivando a performance</p>
			<p>&bull;  Evite QUERY HINTS (comum em Oracle)</p>
			<p>&bull;  Use subqueries correlatas</p>
			<pre class="brush: sql;">
			select	*
			from	Tabela
			where	Campo = 123;</pre>
		</div>

		<div class="step slide" data-x="3000" data-z="500" data-rotate-y="20">
			<h1>Tabelas Temporárias</h1>
			<q>#Local</q>
			<p>Visibilidade restrita, conexão atual</p>
			<q>##Global</q>
			<p>Visíveis por todas as conexões</p>
			<pre class="brush: sql;">
			if ( exists (
				select	top 1 1
				from	Tempdb..SysObjects
				where	Name like '##TabelaTemporaria%' ) ) begin
				drop table ##TabelaTemporaria;
			end;</pre>
		</div>

		<div class="step slide" data-x="4000">
			<q>TempDB</q>
			<pre class="brush: sql;">
			create #Tabela (
				campoA varchar(16),
				campoB int
			)

			create ##Tabela (
				campoA varchar(16),
				campoB int
			)
			select	p.Nome
			,		p.DataNascimento
			into	#Tabela
			from	Pessoas p
			where	p.Sexo = 'M'</pre>
			Tabelas temporárias permitem criação de índices.
			<img src="img/tempdb.PNG" style="position: relative; top: -400px; left: 265px; width: 300px;">
			
		</div>

		<div class="step slide"  data-x="5000" data-z="500">
			<q>Variáveis de Tabela</q>
			&bull; Escopo: conexão atual em tempo de execução<br/>
			&bull; Não permitem criação de índice<br/>
			&bull; Dificuldade de debug<br/>
			<pre class="brush: sql;">
			declare @Tabela table (
				campoA smalldatetime,
				campoB int
			)

			insert into @Tabela (campoA, campoB)
				select	nf.DataEmissao
				,		inf.Codigo
				from	NotasFicais nf
				join	ItensNotaFical inf
						on nf.IdNotaFiscal = inf.IdNotaFiscal</pre>
		</div>
		
		<div class="step slide"  data-x="6000">
			<q>Qual usar?</q>
			<br/>
			<b>Necessito de estatísticas e plano de execução eficientes?</b>
			<br/>
			Tabelas temporárias - possuem estatísticas
			<br/>
			Variáveis de tabelas - não possuem estatísticas
			<br/>
			Geralmente procedimentos (procedure) utilizam plano de execução em Cache, com o uso de tabelas temporárias é forçada uma nova compilação.
			<br/>
			
			<br/>
			<p><span class="texto-azul">Não utilize</span> variáveis de tabela <br/> para armazenar mais de <span class="texto-vermelho">100 linhas</span></p>
			<br/>
		</div>
		
		<div class="step slide"  data-x="7000" data-z="1200" data-rotate-x="-30">
			<q>WITH common_table_expression</q>
			&bull; CTE - expressão de tabela comum <br/>
			&bull; Pode ser utilizada com SELECT, INSERT, UPDATE e DELETE <br/>
			&bull; Muito usado para recursão <br/>
			<br/>
			<img src="img/with_001.PNG" style="width: 800px;">
		</div>

		<div class="step slide"  data-x="7000" data-z="1200" data-y="5000" data-rotate-x="-30">
			<b>Recursividade</b>
			<br/><br/>
			<img src="img/with_002.PNG">
		</div>
		
		<div class="step slide"  data-x="7000" data-z="500" data-rotate-x="30">
			<q><i>char, nchar, varchar</i> e <i>nvarchar</i></q>
			<br/>
			<table>
				<tr>
					<th>Tipo</th>
					<th>Unicode</th>
					<th>Tamanho</th>
				</tr>
				<tr>
					<td>nchar</td>
					<td>Sim</td>
					<td>Fixo</td>
				</tr>
				<tr>
					<td>nvarchar</td>
					<td>Sim</td>
					<td>Variável</td>
				</tr>
				<tr>
					<td>char</td>
					<td>Não</td>
					<td>Fixo</td>
				</tr>
				<tr>
					<td>varchar</td>
					<td>Não</td>
					<td>Variável</td>
				</tr>
			</table>
			
			<br/>
			&bull; <b>fixo</b> reserva o espaço de memória mesmo que não seja utilizado<br/>
			&bull; <b>variável</b> ocupa o espaço do que foi utilizado<br/>
			&bull; <b>unicode</b> representar e manipular, de forma consistente, texto de qualquer sistema de escrita existente<br/>
		</div>		

		<div class="step slide"  data-x="8000" data-y="3000" data-rotate-x="180">
			<q>RAISERROR</q>
			<div style="font-size: 25px;">
				<pre class="brush: sql;">
				begin try
					declare @result INT			
					set @result = 55/0 --Divide-by-zero error
				end try
				begin catch
					--Get the details of the error
					--that invoked the CATCH block
					declare		@ErMessage nvarchar(2048)
					,			@ErSeverity int
					,			@ErState int;
				 
					select	@ErMessage = ERROR_MESSAGE()
					,		@ErSeverity = ERROR_SEVERITY()
					,		@ErState = ERROR_STATE();
				 
					raiserror (@ErMessage, @ErSeverity, @ErState)
				end catch
				
				--RESULT:
				--Msg 50000, Level 16, State 1, Line 16
				--Divide by zero error encountered.</pre>
			</div>
		</div>

		<div class="step slide"  data-x="8000" data-y="4000" data-rotate-x="180">
			<q>THROW</q>
			<pre class="brush: sql;">
			begin try
			  declare @result int
			  set @result = 55/0 --Divide-by-zero error
			end try
			begin catch
				throw
			end catch

			--RESULT:
			--Msg 8134, Level 16, State 1, Line 3
			--Divide by zero error encountered.</pre>			
		</div>

		<div class="step slide"  data-x="8000" data-y="5000" data-rotate-x="180">
			Interrompe a execução?
			<div style="font-size: 25px;">
				<pre class="brush: sql;">
				begin
					print 'BEFORE RAISERROR'
					raiserror('RAISERROR TEST',16,1)
					print 'AFTER RAISERROR'
				end
				
				--RESULT:
				--BEFORE RAISERROR
				--Msg 50000, Level 16, State 1, Line 3
				--RAISERROR TEST
				--AFTER RAISERROR</pre>

				<pre class="brush: sql;">
				begin
					print 'BEFORE THROW';
					throw 50000,'THROW TEST',1
					print 'AFTER THROW'
				end
				
				--RESULT:
				--BEFORE THROW
				--Msg 50000, Level 16, State 1, Line 3
				--THROW TEST</pre>
			</div>
		</div>
		
		<div class="step slide"  data-x="9000" data-z="500">
			<b>ROLLUP e CUBE</b><br/>
			Comandos de totalização<br/><br/>
			<img src="img/cube_rollup_001.PNG" style="width: 500px; ">
		</div>

		<div class="step slide"  data-x="9000" data-y="-1000" data-z="500">
			<b>ROLLUP</b>
			<br/>
			<img src="img/cube_rollup_002.PNG" style="width: 500px; ">
		</div>

		<div class="step slide"  data-x="9000" data-y="-2000" data-z="500">
			<b>CUBE</b>
			<br/>
			<img src="img/cube_rollup_003.PNG" style="width: 500px; ">
		</div>

		<div class="step slide"  data-x="10000" data-rotate-x="30">
			<q>PIVOT e UNPIVOT</q>
			Transforma linhas em colunas e vice-versa.<br/><br/>
			<img src="img/pivot_001.PNG" style="width: 800px; ">
		</div>

		<div class="step slide"  data-x="10000" data-y="-1000" data-rotate-x="30">
			<q>PIVOT</q><br/>
			<img src="img/pivot_002.PNG" style="width: 900px; ">
		</div>

		<div class="step slide"  data-x="12000" data-rotate-x="30">
			<h1>Coluna Calculada</h1>
			&bull; É uma coluna virtual.<br/>
			&bull; Não está fisicamente armazenada na tabela <b>*PERSISTED*</b><br/>
			&bull; Se baseia em dados que já existem.<br/>
			&bull; <b>DEFAULT</b>, <b>FOREIGN KEY</b> e <b>NOT NULL</b> - não pode ser usada<br/>
			<pre class="brush: sql;">
			ALTER TABLE dbo.Produto
			ADD ValorTotal AS (Quantidade * ValorUnitario * 1.5)</pre>
		</div>

		<div class="step slide"  data-x="16000" data-z="500">
			<b>UNION e UNION ALL</b><br/><br/>
			<img src="img/sql_001.PNG" style="position: relative; top: 0px; left: 0px; ">
			<img src="img/sql_002.PNG" style="position: relative; top: 40px; left: -180px; ">
			<img src="img/sql_003.PNG" style="position: relative; top: -240px; left: 180px; ">
		</div>
		
		<div class="step slide"  data-x="17000" data-rotate-x="30">
			<b>EXCEPT</b><br/><br/>
			<img src="img/sql_001.PNG" style="position: relative; top: 0px; left: 0px; ">
			<img src="img/sql_004.PNG" style="position: relative; top: 40px; left: -180px; ">
			<img src="img/sql_005.PNG" style="position: relative; top: -180px; left: 180px; ">
		</div>
		
		<div class="step slide"  data-x="18000" data-z="500">
			<b>INTERSECT</b><br/><br/>
			<img src="img/sql_001.PNG" style="position: relative; top: 0px; left: 0px; ">
			<img src="img/sql_006.PNG" style="position: relative; top: 40px; left: 0px; ">
		</div>

		<div class="step slide"  data-x="11000" data-z="500">
			<h1>Recapitulando</h1>
			&bull; UNION - combina resultados = distinct + order by<br/>
			&bull; UNION ALL - combina resultados (mais rápido)<br/>
			&bull; EXCEPT - Um conjunto menos o outro<br/>
			&bull; INTERSECT - Igual nos dois<br/>
			<br/>
			<img src="img/conjunto.jpg">
		</div>		

		<div class="step slide"  data-x="19000" data-y="-2000">
			<b>MERGE</b><br/>
			<br/>
			&bull; Insert, Update e/ou Delete - tudo junto e reunido
			<pre class="brush: sql;">
				merge  dbo.Titulos as T
				using  @Tab as S on (T.IdTitulo = S.IdTitulo)
				when matched and (T.Nome != S.Nome) then 
					update set T.Nome = S.Nome
				when not matched by Target then
					insert (NumeroTitulo, Nome, Valor, DataInclusao) 
					values (999, S.Nome, 0, getdate())
				when not matched by Source then 
					delete
				output $action, 
				DELETED.IdTitulo as TargetIdTitulo, 
				INSERTED.IdTitulo as TargetIdTitulo;</pre>
		</div>
		
		<div class="step slide"  data-x="19000" data-y="-4000">
			<h1>WITH (NOLOCK)</h1>
			
			&bull; SQL Server 2000 - a própria Microsoft recomendava o uso do <b>NOLOCK</b><br/>
			&bull; O uso indiscriminado do With(Nolock) pode gerar erros transitórios.<br/>
			&bull; <b>SELECT</b> em conjunto com <b>UPDATE</b> e/ou <b>DELETE</b><br/>
			&bull; SQL Server 2005/2008 - solução mais elegante <br/><b>READ COMMITTED SNAPSHOT</b><br/>
			&bull; Configuração do banco de dados e não necessita alteração em código.<br/>
			&bull; Mantém as versões em <b>tempdb</b>.
		</div>
		
		<div class="step slide"  data-x="19000">
			<h1>PRIMARY KEY <br/> UNIQUE KEY</h1>
			<table>
				<tr>
					<th style="width: 20%;"></th>
					<th>Primary Key</th>
					<th>Unique Key</th>
				</tr>
				<tr>
					<td>NULL</td>
					<td>Não</td>
					<td>Sim</td>
				</tr>
				<tr>
					<td>INDEX</td>
					<td>Default clustered index</td>
					<td>Default non-clustered index</td>
				</tr>
				<tr>
					<td>LIMITE</td>
					<td>1</td>
					<td>1 ou +</td>
				</tr>
			</table>
			<br/>
			<b>*Ambos não permitem valores duplicados</b>
			<br/>
			<br/>
			Exemplo tabela de Pessoas : Primary Key <b>Id</b> - Unique Key <b>CPF</b>
		</div>

		<div class="step slide"  data-x="13000">
			<b>DATETIME e DATETIME2</b><br/><br/>
			<table>
				<tr>
					<th style="width: 20%;"></th>
					<th style="width: 33%;">DateTime</th>
					<th style="width: 33%;">DateTime2[(n)]</th>
				</tr>
				<tr>
					<td>Min Value</td>
					<td>1753-01-01 00:00:00</td>
					<td>0001-01-01 00:00:00</td>
				</tr>
				<tr>
					<td>Max Value</td>
					<td>9999-12-31 23:59:59.997</td>
					<td>9999-12-31 23:59:59.9999999</td>
				</tr>
				<tr>
					<td>Storage Size</td>
					<td>8 Bytes</td>
					<td>6 to 8 bytes</td>
				</tr>
				<tr>
					<td>Usage</td>
					<td>Declare @now datetime</td>
					<td>Declare @now datetime2(7)</td>
				</tr>
				<tr>
					<td>Current Date </td>
					<td>GetDate()</td>
					<td>SYSDATETIME()</td>
				</tr>
				<tr>
					<td>+/- days</td>
					<td>Works <br/> select getdate() + 1 </td>
					<td>Fail - need to use only DateAdd function <br/> select dateadd(day, 1, sysdatetime()) </td>
				</tr>
			</table>
		</div>
		
		<div class="step slide"  data-x="14000" data-z="500">
			<h1>Check Constraint</h1>
			&bull; Integridade dos dados<br/>
			&bull; Evita tabela de domínio<br/>
			&bull; Exige cuidado e manutenção<br/>
			<pre class="brush: sql;">
			ALTER TABLE dbo.Pessoa
			ADD Sexo char(1) CHECK ( Sexo in ('M', 'F') )</pre>
			<pre class="brush: sql;">
			ALTER TABLE dbo.Produto
			ADD Validade int CHECK (
				Validade >= 1 and Validade < 13
			)</pre>
		</div>	

		<div class="step slide" data-x="1000" data-z="500">
			<h1>Otimizador de Consultas</h1>
			<q>Estatísticas</q>
			<p>Número de registros, índices, chaves e cardinalidade das tabelas.</p>
			<q>Plano de Execução</q>
			<p>Menor custo (CPU e IO) e tempo.</p>
			<br />
			<img width="800px;" src="img/plano.png">
		</div>
		
		<div class="step slide"  data-x="9000" data-y="-1000" data-rotate-x="90" data-rotate-z="90">
			<q>Boas Práticas 01</q>
			<br/>
			&bull; Normalize - basicamente divida tabelas grandes em tabelas menores e remova redundância
			<br/><br/>
			&bull; Evite tabelas resultado ou totalizadoras
			<br/><br/>
			&bull; Utilize transações, vários problemas podem ocorrer
			<br/><br/>
			&bull; Evite a utilização do SELECT * - traga somente o que for utilizar
			<br/><br/>
			&bull; INSERT - específique os campos inseridos
			<pre class="brush: sql;">
			insert into dbo.Tabela (Campo1, Campo2)
			select Valor1, Valor2 from dbo.OutraTabela</pre>			
		</div>

		<div class="step slide"  data-x="9000" data-y="1000" data-rotate-x="30">
			<q>Boas Práticas 02</q><br/>
			&bull; Evite uso de cursores - podemos usar variável de tabela (lógica de conjunto)
			<br/><br/>
			&bull; Tratamento de erros <b>TRY</b> e <b>CATCH</b>
			<br/><br/>			
			&bull; Usar o <b>THROW</b> ao invés de <b>RAISERROR</b>
			<br/><br/>
			&bull; Usar <b>JOIN</b> ao invés de <b>SUB-QUERIES</b>
			<br/><br/>			
			&bull; Usar <b>ORDER BY</b>, <b>DISTINCT</b> e <b>TOP</b> somente quando necessário
			<br/><br/>
			&bull; Em geral <b>EXISTS</b> e <b>IN</b> são mais eficiente que <b>NOT EXISTS</b> e <b>NOT IN</b><br/>
			Moldar a consulta para usar o mais eficiente
		</div>

		<div class="step slide"  data-x="9000" data-y="2000" data-rotate-x="30">
			<q>Boas Práticas 03</q><br/>
			&bull; Utilize o <b>EXISTS</b> em conjunto com o <b>SELECT TOP 1</b>
			<br/>
			&bull; Utilize o <b>EXISTS</b> ao invés de <b>COUNT</b> para teste de existência<br/>
			&bull;  <b>EXISTS</b> pára a execução quando encontra o primeiro e o <b>COUNT</b> continua a execução até o último registro
			<br/><br/>
			
			<pre class="brush: sql;">
			if ( exists ( select top 1 1 from dbo.Pagamentos )) begin
				print 'ok'
			end</pre>
			&bull; Quando usar <b>LIKE</b> procure utilizar:<br/>
			<pre class="brush: sql;">
				where Campo LIKE '%Fula%' --não usa índice
				where Campo LIKE 'Fula%' --usa índice</pre>
		</div>

		<div class="step slide"  data-x="10500" data-y="2000" data-rotate-x="30">
			<q>Boas Práticas 03.1</q><br/>
			&bull; Usar o <b>@@ROWCOUNT</b> e <b>@@ERROR</b> após a execução de um comando
			
			<pre class="brush: sql;">
			insert into dbo.Cidades (Nome)
			values ('Porto Alegre')
			,      ('Cachoeirinha');

			select @@rowcount;

			--RETURN:
			--2
			
			select @@error;
			--RETURN:
			--0</pre>			
		</div>
		
		<div class="step slide"  data-x="12000" data-y="2000" data-rotate-x="30">
			<q>Boas Práticas 03.2</q><br/>		
			&bull; Usar o <b>scope_identity()</b> após uma inserção para retornar o identity
			
			<pre class="brush: sql;">
			insert into dbo.Titulos (NumeroTitulo, Nome, Valor, DataInclusao)
			values ('987654321', 'Juca', 55.25, sysdatetime())

			select scope_identity();
			--RETURN:
			--4</pre>
			
			&bull; Usar <b>with(nolock)</b> ao invés de <b>(nolock)</b><br/>
			Será descontinuado, pode virar alias, dá erro em hint composto
			<br/><br/>
			&bull; Ao invés de <b>where idade > 3</b> use <b>where idade >= 4</b> *se o campo possuir índice
			<br/><br/>
			&bull; Usar <b>";"</b> para fechar um comando
			<br/>
			<br/>
		</div>
		
		<div class="step slide"  data-x="1000" data-y="3000" data-rotate-x="-30">
			<q>Boas Práticas 04</q><br/>
			&bull; Usar o <b>EOMONTH</b> - buscar o último dia do mês
			<pre class="brush: sql;">
			select sysdatetime(); --2017-06-05 10:10:11.7864377
			select eomonth(sysdatetime()); --2017-06-30</pre>
			<br/>
			&bull; Evitar SQL dinâmico - o plano de execução do procedimento não será reutilizado
			<pre class="brush: sql;">
			declare @sql varchar(max)
			,		@tabela varchar(32);
			
			set		@tabela = 'dbo.Cautelas';
			set		@sql = 'select Nome from ' + @tabela + ' where NumeroProposta = 1020;';

			exec    (@sql);</pre>
			<br/><br/>
		</div>
		
		<div class="step slide"  data-x="9000" data-y="4000" data-rotate-x="-60">
			<q>Boas Práticas 05</q><br/>
			&bull; Evite usar operadores de conversão em campos com índices (ele não será utilizado)
			<br/><br/>
			<img src="img/plano_exec.PNG">
		</div>

		
		<div class="step" data-x="-1000" data-y="100" data-z="1000" data-rotate-x="-40" data-rotate-y="10" data-scale="2">
			<img src="img/thks.gif" style="width: 400px;">
			<!-- <span class="footnote">Muito obrigado! <br/> :)</span> -->
		</div>
		
		<div id="overview" class="step" data-x="3000" data-y="0" data-scale="10">
		</div>

	</div>
	
	<div class="hint">
		<p>Use a barra de espa谳 e as setas para navegar</p>
	</div>
	
	<script>
		if ("ontouchstart" in document.documentElement) { 
			document.querySelector(".hint").innerHTML = "<p>Tap on the left or right to navigate</p>";
		}
	</script>
	
	<script src="js/impress.js"></script>
	<script>impress().init();</script>

</body>
</html>
