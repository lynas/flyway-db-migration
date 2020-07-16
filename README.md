# flyway-db-migration

1. add following to application.properties 
```
spring.datasource.url=jdbc:mysql://localhost:3307/flyway_demo
spring.datasource.username=root
spring.datasource.password=password
```
2. Add plugin and override flyway task in build.gradle
```
id("org.flywaydb.flyway") version "6.5.0"

flyway {
	url = "jdbc:mysql://localhost:3307/flyway_demo"
	user = "root"
	password = "password"
}
```
3. File name formate under `src/main/resource/db/migration

```
<Prefix><Version>__<Description>.sql

V1_0__init.sql
```

4. Sample migration script
```
alter table book add column name varchar (200) null ;
```

5. If you do not want automatic db migration when running the application

```
  @Bean
	public FlywayMigrationStrategy flywayMigrationStrategy(){
		return args ->{};
	}
```


