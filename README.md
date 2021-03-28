# test
- django test repository


### docker clean
```
docker rm $(docker ps -q) -f
docker rmi $(docker images -q) -f
```

### chmod
```
chmod +x entrypoint.sh
```

# docker command

### build
```
docker-compose -f docker-compose.yml up -d --build --remove-orphans
```

### check
```
docker-compose -f docker-compose.yml ps -a
```

### db
```
docker-compose -f docker-compose.yml exec django python manage.py flush --no-input
docker-compose -f docker-compose.yml exec django python manage.py makemigrations
docker-compose -f docker-compose.yml exec django python manage.py migrate
```

### static
```
docker-compose -f docker-compose.yml exec django python manage.py collectstatic --no-input --clear
```

### add base data
```
docker-compose -f docker-compose.yml exec django python manage.py loaddata data.json
```

### admin
```
docker-compose -f docker-compose.yml exec django python manage.py createsuperuser
```
http://localhost:1337/admin/login/

### all delete
```
docker-compose -f docker-compose.yml down --rmi all --volumes --remove-orphans
```
