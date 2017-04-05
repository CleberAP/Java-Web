# Projeto Front-End com java.

## Instalando o java 8


Acesse o link http://www.oracle.com/technetwork/pt/java/javase/downloads/index.html

Clique em Java Platform (JDK), escolha seu sistema operacional para instala��o.

 ` Windows ` - Somente siga clicando em Next.

Configurando as Vari�veis de ambiente.
 
```
INICIAR - (clique com o bot�o direito do mouse sobre simbolo do computador e escolha) PROPRIEDADE

CONFIGURA��ES AVAN�ADAS DO SISTEMA - VARI�VEIS DE AMBIENTE


```
Criando Vari�veis de ambiente

```
Clique em ` NOVO `
 
 Nome da vari�vel: JAVA_HOME
 Valor da Vari�vel: C:\Program Files\Java\jdk1.8.0_111   (Caminho da Instala��o do java)

```




## Instalando o eclipse
## Instalando o MySql
## Baixando os jar necess�rios atrav�s do Maven

Criar um pasta `WEB-INF` para conter `web.xml`

```
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns="http://xmlns.jcp.org/xml/ns/javaee"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
	id="WebApp_ID" version="3.1">

	<!-- Nome da Aplica��o -->
	<display-name>Drogaria</display-name>
</web-app>

``` 

Gerando aplica��o para final `Maven Install`


Configurando o pom.xml

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>br.com.drogaria</groupId>
	<artifactId>Drogaria</artifactId>
	<version>1.0</version>
	<packaging>war</packaging>

	<!-- Codifica��o dos caracteres -->
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>

	<!-- Par�metros de execu��o -->
	<build>
		<!-- Nome do projeto empacotado -->
		<finalName>Drogaria</finalName>

		<!-- Plugins -->
		<plugins>
			<!-- Compilador -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.3</version>
				<configuration>
					<source>1.8</source>
					<target>1.8</target>
				</configuration>
			</plugin>
		</plugins>
	</build>

	<!-- Depend�ncias necess�rias -->
	<dependencies>
		<!-- Hibernate Core -->
		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>5.2.9.Final</version>
		</dependency>

		<!-- Conector MySql -->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>6.0.6</version>
		</dependency>

		<!-- Junit na Vers�o 4.12 e 11 aparecem erros-->
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.10</version>  
		</dependency>

	</dependencies>
</project>

```

## Hibernate Config.


Configurando o arquivo hibernate.cfg.xml que fica dentro de src/main/resources

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>

	<session-factory>

		<!-- Configura��es de Conex�o com o Banco de Dados -->
		<property name="connection.driver_class">com.mysql.jdbc.Driver</property>
		<property name="hibernate.connection.url">jdbc:mysql://127.0.0.1:3306/newdrogaria?useTimezone=true&amp;serverTimezone=UTC&amp;useSSL=false</property>
		<property name="connection.username">root</property>
		<property name="connection.password">q1w2e3r4</property>

		<!-- Pool de Conex�es -->
		<property name="connection.pool_size">1</property>

		<!-- SQL dialect -->
		<property name="dialect">org.hibernate.dialect.MySQL5InnoDBDialect</property>

		<!-- Gerenciamento do Contexto das Sess�es -->
		<property name="current_session_context_class">thread</property>

		<!-- Cache de Segundo N�vel -->
		<property name="cache.provider_class">org.hibernate.cache.internal.NoCacheProvider</property>

		<!-- Mostra as SQLs Geradas -->
		<property name="show_sql">true</property>

		<!-- Cria as tabelas do banco de dados -->
		<property name="hbm2ddl.auto">create</property>
		
		<!-- Mapeamento das entidades -->
		
		<mapping class="br.com.drogaria.domain.Estado"/>
		<mapping class="br.com.drogaria.domain.Cidade" />
		<mapping class="br.com.drogaria.domain.Pessoa"/>
		<mapping class="br.com.drogaria.domain.Cliente" />
		<mapping class="br.com.drogaria.domain.Funcionario" />
		<mapping class="br.com.drogaria.domain.Usuario"/>
		
		<mapping class="br.com.drogaria.domain.Fabricante"/>
		<mapping class="br.com.drogaria.domain.Produto"/>
				
		<mapping class="br.com.drogaria.domain.Venda"/>
		<mapping class="br.com.drogaria.domain.ItemVenda"/>
		
	</session-factory>

</hibernate-configuration>

```
