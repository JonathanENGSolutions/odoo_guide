# Odoo 17 Installation guide - Nov 2024
## Update Linux dependences

`sudo apt update`<br>
`sudo apt upgrade`

## Creation of an exclusive user to manage odoo
`sudo adduser --system --quiet --shell=/bin/bash --home=/opt/odoo --gecos 'odoo_user' --group odoo_user`<br>
`sudo passwd odoo_user`

## Installation of packages: Postgre, Node, Git & Python<br>
Verify PostgreSQL version.<br><br>
`sudo apt install postgresql postgresql-server-dev-16 git python3 python3-pip build-essential python3-dev libldap2-dev libsasl2-dev python3-setuptools libjpeg-dev nodejs npm postgresql-client -y`

## Clone latest version of odoo
`sudo git clone --depth 1 --branch 17.0 https://github.com/odoo/odoo /opt/odoo`<br>

In case of error: already exists, delete '.bash_history' and try again.<br><br>
`sudo rm /opt/odoo/.bash_history`

## Change owner root -> odoo_user
`sudo ls /opt/odoo -la` <br>
`sudo chown odoo_user:odoo_user /opt/odoo -R`<br>
`sudo ls /opt/odoo -la`

## Creation of a directory for logging and change of ownership
`sudo mkdir /var/log/odoo/`<br>
`sudo chown odoo_user:odoo_user /var/log/odoo/ -R`

## Install interfaz C for Python
`sudo pip3 install cffi --break-system-packages`<br>
`sudo rm /usr/lib/python3/dist-packages/_cffi_backend.cpython-310-x86_64-linux-gnu.so`<br><br>
Try again

## Odoo dependencies installation
`sudo pip3 install -r /opt/odoo/requirements.txt`
