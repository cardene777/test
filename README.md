# test
django test repository

# docker command

### build
docker-compose -f docker-compose.development.yml up -d --build

### check
docker-compose -f docker-compose.development.yml ps -a

### db
docker-compose -f docker-compose.development.yml exec app python manage.py flush --no-input
docker-compose -f docker-compose.development.yml exec app python manage.py makemigrations
docker-compose -f docker-compose.development.yml exec app python manage.py migrate

### static
docker-compose -f docker-compose.development.yml exec app python manage.py collectstatic --no-input --clear

### admin
docker-compose -f docker-compose.development.yml exec app python manage.py createsuperuser  
http://localhost:1337/admin/login/
