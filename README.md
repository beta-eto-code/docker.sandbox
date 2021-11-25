# docker.sandbox
конфиг для локальной песочницы на докере (подходит для битрикса)

### проверено только для php7.4 + nginx + mysql

### где что
конфиг docker-compose - /docker-compose.yml

конфиг контейнера с php, самого php с xdebug- /php74/Dockerfile и /php74/php.ini

конфиг msmtp - /php74/msmtprc

конфиг mysql - /mysql

логи - /logs

пример env - /.env_template

### как развернуть новый проект
допустим, папка вашего проекта в ~/dev/myproject/
1. кладёте этот реп в ~/dev/myproject/docker/
2. кладёте сам проект в ~/dev/myproject/www/
3. копируете .env_template в .env, меняете там название проекта на своё
4. запускаете докер из папки докера `docker-compose up --build`


### что ещё есть
есть xdebug, конфиг в /php74/php.ini, может работать с phpstorm/intellij

есть mailcatcher (перехват писем), открывается по localhost:1080

###команды
зайти в докер, где сайт с пхп (где myproject - название проекта из env)
```shell
docker exec -ti myproject_php_1 bash
```
импорт дампа бд (где myproject - название проекта из env)
```shell
docker exec -i myproject_db_1 mysql -u bitrix -p123 bitrix < dump.sql
```