Installation
============

Openresty
  Voir :  http://openresty.org/en/linux-packages.html#debian :
  Pre-requis :
    > sudo apt-get install libpcre3-dev libssl-dev perl make build-essential curl

  Configurer dans la machine le fournisseur de module openresy :
    > echo "deb http://openresty.org/package/debian $codename openresty"
    > echo "deb http://openresty.org/package/debian $codename openresty"     | sudo tee /etc/apt/sources.list.d/openresty.list
    > sudo apt-get update

  Installer openresty
    > sudo apt-get -y install openresty

dyndns
    >systemctl start systemd-resolved.service


