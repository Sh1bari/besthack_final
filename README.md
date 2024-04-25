# RT5_BestHack_24
- [Service monitoring](http://62.217.182.34:8111/admin-ui/applications)
- [Service registry](http://62.217.182.34:8111/eureka-ui)
- [Authorization service swagger](http://62.217.182.34:8111/api/auth/swagger-ui/index.html#/)
- [Main service swagger](http://62.217.182.34:8111/api/main/swagger-ui/index.html#/)

## Состав команды:
- Таланкина Варвара: Тимлид-команды
- Краснов Владимир: Java бекенд-разработчик
- Аюшиев Тимур: Фронтенд-разработчик
- Толкачев Родион: Фронтенд-разработчик

В рамках хакатона была написана CMS-система для уведомлений пользователей, в качестве референса использовали open-source CMS Orchard Core.

# Backend

## ApiGateway
- Spring cloud gateway
- Spring admin
- [Service monitoring](http://62.217.182.34:8111/admin-ui/applications)
- Actuator

## Service registry
- Spring Eureka
- [Service registry](http://62.217.182.34:8111/eureka-ui)
- Actuator

## Authorization service
- [Authorization service swagger](http://62.217.182.34:8111/api/auth/swagger-ui/index.html#/)
- Spring security + jwt (key pair)
- PostgreSql
- Feign
- Log4j
- Spring validation
- Actuator
!(https://github.com/Sh1bari/RT5_BestHack_24/blob/main/auth.png)

## Main service
- [Main service swagger](http://62.217.182.34:8111/api/main/swagger-ui/index.html#/)
- Spring security + jwt (public key)
- PostgreSql
- Feign
- Spring validation
- Firebase admin
- Actuator
!(https://github.com/Sh1bari/RT5_BestHack_24/blob/main/main.png)

## Deploy
- Beget host
- Nginx
- SSH tunnel

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

Для реализации механизма уведомлений использовалась firebase notification, которая позволяет получать уведомления в фоновом режиме, а при перемещении по приложению. 

Фичи:
- Конструктор уведомлений. В зависимости от содержания, уведомление будет помеченно определенным цветом и будет определена возможность его закрыть:

"Важно ..." : пометка оранжевым, нельзя закрыть
"Срочно ...": пометка красным, нельзя закрыть
любое другое: пометка зеленым, закрыть можно

- Связи департаментов. С помощью библиотеки react-graph-vis был реализован граф, по которому можно определить из какого, в какой департамент может отправлять сотрудник уведомления.

- История конкретного пользователя. В профиле пользователь может увидеть свою историю уведомлений, все уведомления, которые он когда-либо отправлял.
