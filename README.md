# RT5_BestHack_24
Данные для входа под админом: string|string
- [Service monitoring](http://62.217.182.34:8111/admin-ui/applications)
- [Service registry](https://my-timecheck.ru/ui/eureka-ui)
- [Authorization service swagger](https://my-timecheck.ru/api/auth/swagger-ui/index.html#/)
- [Main service swagger](https://my-timecheck.ru/api/main/swagger-ui/index.html#/)

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
- [Service monitoring](https://my-timecheck.ru/admin-ui/applications)
- Actuator

## Service registry
- Spring Eureka
- [Service registry](https://my-timecheck.ru/eureka-ui)
- Actuator

## Authorization service
- [Authorization service swagger](https:my-timecheck.ru/api/auth/swagger-ui/index.html#/)
- Spring security + jwt (key pair)
- PostgreSql
- Feign
- Log4j
- Spring validation
- Actuator<br/>
![Database](https://github.com/Sh1bari/RT5_BestHack_24/blob/main/auth.png)

Для запуска в postgres добавить пользователя root, пароль 123, от него создать бд Time-tracker-auth

## Main service
- [Main service swagger](https://my-timecheck.ru/api/main/swagger-ui/index.html#/)
- Spring security + jwt (public key)
- PostgreSql
- Feign
- Spring validation
- Firebase admin
- Actuator<br/>
![Database](https://github.com/Sh1bari/RT5_BestHack_24/blob/main/main.png)

Для запуска в postgres добавить пользователя root, пароль 123, от него создать бд main-db

## Deploy
- Beget host
- Nginx
- SSH tunnel
- Sertbot

## Ролевая система
Приложение расчитано на 1 организацию, главный - админ
Админ может создавать департаменты и добавлять в них пользователей\сотрудников
Пользователи могут только получать уведомления
Сотрудники получать и отправлять

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

## Как пользоваться приложением?

Если вы обычный пользователь, то после регистрации или авторизации вы сразу попадете в свой профиль, где сможете просматривать свои уведомления.

Если вы администратор, то после регистрации или авторизации вы попадете на главную страницу, где перед вами окажется история абсолютно всех уведомлений, выше вы можете выбирать фильтры с помощью выпадающих списков.
Вкладка управление отвечает за возможность создания и редактирования департаментов, вклдака "создать уведомление" отвечает за конструктор уведомления, откуда вы сможете рассылать уведомления, на вкладке департаменты вы сможете увидеть связи департаментов по возможности отправлять друг другу уведомления.

Если вы сотрудник, то вы сможете взаимодействовать с вкладками создания уведомления, если у вас есть на то доступ, либо с вкладкой департаментов.

При запуске с docker-compose
- [Frontend](http://localhost:3000)
- [Service monitoring](http://localhost:8111/admin-ui/applications)
- [Service registry](http://localhost:8111/eureka-ui)
- [Authorization service swagger](http://localhost:8111/api/auth/swagger-ui/index.html#/)
- [Main service swagger](http://localhost:8111/api/main/swagger-ui/index.html#/)

После старта докера
```bash
podman exec -it my-postgres-auth bash
psql -U postgres -d Time-tracker-auth
INSERT INTO roles (name) VALUES ('ROLE_USER');
\q
exit
podman exec -it my-postgres bash
psql -U postgres -d main-db
SELECT * FROM users;
UPDATE users SET global_role = 'ROLE_ADMIN' WHERE id = 'ваш-id';
```
