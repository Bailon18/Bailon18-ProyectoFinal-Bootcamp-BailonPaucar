# Sistema Bancario - Proyecto de Microservicios 

Este repositorio contiene la documentación y los diagramas UML del proyecto del sistema bancario basado en microservicios. El proyecto se compone de cuatro servicios:

1. **TransaccionMS**: Microservicio para la gestión de Transacciones Bancarias.
2. **CustomerMS**: Microservicio para la gestión de clientes.
3. **AccountMS**: Microservicio para la gestión de cuentas bancarias.
4. **Eureka Server**: Servicio de registro para la gestión y descubrimiento de microservicios.

## Diagramas UML
El repositorio incluye los siguientes diagramas:

- **Diagrama de Caso de Uso**
- **Diagrama de Secuencia**
- **Diagrama de Componentes**

## Reportes y Pruebas

### 1. Reporte de Cobertura con JaCoCo
El proyecto incluye un reporte de cobertura de código generado con JaCoCo. Este reporte detalla la cobertura de los test unitarios para cada microservicio, mostrando el porcentaje de líneas y ramas cubiertas en cada componente del sistema.

- **Reporte de Cobertura**: Ubicado en la carpeta `REPORTE JACOCO`.

### 2. Pruebas en Postman
Se ha preparado una colección de Postman que incluye pruebas para los tres microservicios (`TransactionMS`, `CustomerMS` y `AccountMS`). Esta colección está lista para ser importada y ejecutada.

- **Colección de Postman**: `Microservicios NTT DATA.POSTMAN.json`. Solo necesitas importarla en tu Postman para utilizarla.

## Estructura del Proyecto
### Microservicios y Servicios
El sistema está compuesto por cuatro servicios independientes:

1. **TransactionMS** - [Click aquí](https://github.com/Bailon18/transaction-ms)
2. **CustomerMS** - [Click aquí](https://github.com/Bailon18/customer-ms)
3. **AccountMS** - [Click aquí](https://github.com/Bailon18/account-ms)
4. **Eureka Server** - [Click aquí](https://github.com/Bailon18/eureka-server)

### Base de Datos
Cada microservicio se conecta a su propia base de datos MySQL alojada en Railway. Las configuraciones ya están predefinidas y no es necesario realizar ajustes adicionales para la conexión a la base de datos.

## Implementación en la Nube
Los microservicios están desplegados en Railway con la documentación de cada servicio disponible a través de Swagger, por lo que pueden ser testeados directamente en la nube utilizando los siguientes enlaces:

- **TransactionMS en la nube**: [Click aquí](https://transaction-ms-production.up.railway.app/swagger-ui/index.html)
- **CustomerMS en la nube**: [Click aquí](https://customer-ms-production.up.railway.app/swagger-ui/index.html)
- **AccountMS en la nube**: [Click aquí](https://account-ms-production.up.railway.app/swagger-ui/index.html)
- **Eureka Server en la nube**: [Click aquí](https://euraka-server-production.up.railway.app/)

## Ejecución Local
Si deseas ejecutar los microservicios localmente, sigue estos pasos:

### Requisitos Previos
- Java 11 o superior
- Maven
- MySQL instalado localmente
- Postman para probar los endpoints

### Instrucciones
1. Clona los repositorios correspondientes:

  ```bash
   git clone https://github.com/Bailon18/transaction-ms
   git clone https://github.com/Bailon18/customer-ms
   git clone https://github.com/Bailon18/account-ms
   git clone https://github.com/Bailon18/eureka-server
   ```

2. Configura las bases de datos locales en el archivo `application.yml` para los microservicios `TransactionMS`, `CustomerMS` y `AccountMS`. Si prefieres utilizar las bases de datos en Railway, no es necesario modificar la configuración.

3. Descomenta las siguientes configuraciones para habilitar la ejecución local:

#### TransactionMS
   - `client/AccountFeign.java` -> Elimina el parámetro `url` en la anotación `@FeignClient` para que apunte a la instancia local.
   - `resources/openapi.yaml` -> Verifica las rutas locales para los servicios.
   - `application.yml` -> Descomenta las siguientes líneas:
     ```yaml
     #defaultZone: http://localhost:8761/eureka/ 
     #hostname: localhost
     ```

#### AccountMS
   - `client/ClienteFeign.java` -> Elimina el parámetro `url` en la anotación `@FeignClient` para que apunte a la instancia local.
   - `resources/static/openapi.yaml` -> Verifica las rutas locales para los servicios.
   - `application.yml` -> Descomenta las siguientes líneas:
     ```yaml
     #defaultZone: http://localhost:8761/eureka/ 
     #hostname: localhost
     ```

#### CustomerMS
   - `client/AccountFeign.java` -> Elimina el parámetro `url` en la anotación `@FeignClient` para que apunte a la instancia local.
   - `resources/static/openapi.yaml` -> Verifica las rutas locales para los servicios.
   - `application.yml` -> Descomenta las siguientes líneas:
     ```yaml
     #defaultZone: http://localhost:8761/eureka/ 
     #hostname: localhost
     ```

#### EurekaServer
   - `application.yml` -> Descomenta las siguientes líneas:
     ```yaml
     #server:
     #  port: 8761
     ```

4. Una vez que los tres servicios estén en ejecución, accede a:

   - **TransactionMS API**: [http://localhost:8084/cuentas](http://localhost:8084/cuentas)
   - **CustomerMS API**: [http://localhost:8082/clientes](http://localhost:8082/clientes)
   - **AccountMS API**: [http://localhost:8081/cuentas](http://localhost:8081/cuentas)
   - **Eureka Dashboard**: [http://localhost:8761/](http://localhost:8761/)

### Probar con Postman
Puedes utilizar Postman para realizar pruebas de los endpoints de cada microservicio. Simplemente importa la colección `Microservicios NTT DATA.POSTMAN.json` y tendrás acceso a todas las pruebas preparadas.
