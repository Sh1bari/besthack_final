# RT5_BestHack_24
## Данные для входа под админом: 

## +76666666666 | 1655

*Работает только для хостинга, для запуска локально информация ниже*
- [Site](https://my-timecheck.ru/)
- [Service monitoring](http://62.217.182.34:8111/admin-ui/applications)
- [Service registry](https://my-timecheck.ru/ui/eureka-ui)
- [Authorization service swagger](https://my-timecheck.ru/api/auth/swagger-ui/index.html#/)
- [Main service swagger](https://my-timecheck.ru/api/main/swagger-ui/index.html#/)

## Состав команды:
- Таланкина Варвара: Тимлид-команды
- Краснов Владимир: Java бекенд-разработчик \ DevOps
- Аюшиев Тимур: Фронтенд-разработчик
- Толкачев Родион: Фронтенд-разработчик

# Backend

## ApiGateway
- Spring cloud gateway
- Spring admin
- Actuator

## Service registry
- Spring Eureka
- Actuator

## Authorization service
- Spring security + jwt (key pair)
- PostgreSql
- Feign
- Log4j
- Spring validation
- Actuator<br/>
![Database](https://github.com/Sh1bari/RT5_BestHack_24/blob/main/auth.png)

## Main service
- [Main service swagger](https://my-timecheck.ru/api/main/swagger-ui/index.html#/)
- Spring security + jwt (public key)
- PostgreSql
- Feign
- Spring validation
- Firebase admin
- Actuator<br/>
![Database](https://github.com/Sh1bari/besthack_final/blob/main/main.png)

## Deploy
- Beget host
- Nginx
- SSH tunnel
- Sertbot
- Docker
- Docker-compose

# Frontend
Стек технологий:
- React v18
- TypeScript
- yarn v1.22.22
- Redux ToolKit v2.2.3
- axios v1.6.8
- react-graph-vis v1.0.7
- SCSS
- Mantine UI
- Firebase v10

При запуске с docker-compose
- [Frontend](http://localhost:3000)
- [Service monitoring](http://localhost:8111/admin-ui/applications)
- [Service registry](http://localhost:8111/eureka-ui)
- [Authorization service swagger](http://localhost:8111/api/auth/swagger-ui/index.html#/)
- [Main service swagger](http://localhost:8111/api/main/swagger-ui/index.html#/)

