php bin/cli.php install --domain=lackky.dev --username=phanbook \
--password=phanbook \
 --email=hello@phanbook.com \
  --private-key=/usr/share/nginx/minds/.dev/minds.pem \
   --public-key=/usr/share/nginx/minds/.dev/minds.pub  


http://downloads.datastax.com/cpp-driver/centos/7/dependencies/libuv/v1.14.1/libuv-1.14.1-1.el7.centos.x86_64.rpm
http://downloads.datastax.com/cpp-driver/centos/7/dependencies/libuv/v1.14.1/libuv-devel-1.14.1-1.el7.centos.x86_64.rpm

   http://downloads.datastax.com/cpp-driver/centos/7/cassandra/v2.7.1/cassandra-cpp-driver-2.7.1-1.el7.centos.x86_64.rpm
   http://downloads.datastax.com/cpp-driver/centos/7/cassandra/v2.7.1/cassandra-cpp-driver-devel-2.7.1-1.el7.centos.x86_64.rpm
pecl install cassandra
   echo "extension=cassandra.so" > /etc/php.d/cassandra.ini


 ansible-playbook -i hosts/local/inventory playbook.yml --tags "neo4j"
