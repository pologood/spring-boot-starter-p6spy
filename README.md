# spring-boot-starter-ip2region
ip2region starter for spring boot

### 说明


 > 基于 ip2region 的 Spring Boot Starter 实现

1. 最新IP数据下载地址： https://github.com/lionsoul2014/ip2region

### Maven

``` xml
<dependency>
	<groupId>com.github.vindell</groupId>
	<artifactId>spring-boot-starter-ip2region</artifactId>
	<version>${project.version}</version>
</dependency>
```

### Sample

```java

import javax.sql.DataSource;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;

import com.p6spy.engine.spy.P6DriverManagerDataSource;
import com.p6spy.spring.boot.ext.P6spyDataSource;

@EnableP6Spy
@SpringBootApplication
public class Application {
	
	@Bean
	@P6spyDataSource
	DataSource dataSource() {
		
		// just demo
		P6DriverManagerDataSource ds =	new P6DriverManagerDataSource();
		ds.setUrl("url");
		ds.setUser("username");
		ds.setPassword("password");
		
		return ds;
	};
	
	public static void main(String[] args) throws Exception {
		SpringApplication.run(Application.class, args);
	}

}

```

如果使用外部IP数据，可自定义配置，参考如下：
```yaml
ip2region:
  external: false
  index-block-size: 4096
  total-header-size: 8192
  location: classpath:ip2region/ip2region.db
```

