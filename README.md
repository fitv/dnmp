# DNMP
Docker LNMP

## Services
- Nginx 1.22
- MySQL 8.0
- PHP 8.1
- Redis 7.0
- Supervisor

## Build or rebuild services
```
docker-compose build
```

## Create and start containers
```
docker-compose up -d
```

## Enter the php container
```
docker-compose exec php bash
```

## Restart containers
```
docker-compose restart
```

## Stop containers
```
docker-compose stop
```

## Stop and remove containers
```
docker-compose down
```
