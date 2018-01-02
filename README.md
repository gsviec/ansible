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

If you verfy false you need consider edit this line [inveter host](https://github.com/gsviec/ansible/blob/master/hosts/local/inventory#L2)

```
web01 ansible_ssh_host=52.203.122.188 ansible_ssh_port=22

```

To be 

```
web01 ansible_ssh_host=xxx.xxx.xxx ansible_ssh_port=22 ansible_ssh_user=vagrant ansible_ssh_pass=vagrant

```

Inside xxx.xxx.xxx is your server, ansible_ssh_user is username your sever. After that running followign command below:

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

```

### Setup minds backend

```
php ./bin/regenerateDevKeys.php;

php bin/cli.php install --domain=lackky.dev --username=phanbook \
--password=phanbook \
 --email=hello@phanbook.com \
  --private-key=/usr/share/nginx/minds/.dev/minds.pem \
   --public-key=/usr/share/nginx/minds/.dev/minds.pub  
```

 mkdir -p /data/glusterfs/bricks

gluster volume create g-wordpress replica 2 transport tcp node2.glusterfs:/data/glusterfs/bricks node1.glusterfs:/data/glusterfs/bricks force

mount.glusterfs node1.glusterfs:/g-wordpress /srv/www

172.31.28.161  node1
172.31.19.213  node2