### Setup server

First you must have ansible, if you have not install it go to [http://ansible.com/](http://ansible.com/) then verify server via

```
git clone https://github.com/gsviec/ansible
cd ansible

ansible all  -m ping -i hosts/local/inventory

web01 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}


```
After that running followign command below:

```
ansible-playbook -i hosts/local/inventory playbook.yml

```



### Setup specific role:

```
ansible-playbook -i hosts/local/inventory playbook.yml --tags "neo4j"

```


### Setup minds frontend

```
cd /usr/share/nginx/
git clone https://github.com/Minds/minds.git
cd minds/ && sh init.sh
cd front
npm install
npm run build
composer install --no-dev
mkdir --parents --mode=0777 /tmp/minds-cache/
mkdir --parents --mode=0777 /data


### Setup minds backend

```
php ./bin/regenerateDevKeys.php;

php bin/cli.php install --domain=lackky.dev --username=phanbook \
--password=phanbook \
 --email=hello@phanbook.com \
  --private-key=/usr/share/nginx/minds/.dev/minds.pem \
   --public-key=/usr/share/nginx/minds/.dev/minds.pub  