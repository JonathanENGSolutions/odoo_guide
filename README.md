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
`sudo pip3 install -r /opt/odoo/requirements.txt --break-system-packages`

## Installation of wkhtmltopdf utility
`sudo apt install fontconfig xfonts-base xfonts-75dpi -y`<br>
Temporary folder to finish the installation:<br>
`cd /tmp`<br>
`wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6.1-3/wkhtmltox_0.12.6.1-3.bookworm_amd64.deb`<br>
`sudo dpkg -i wkhtmltox_0.12.6.1-3.bookworm_amd64.deb`<br>
`sudo ln -s /usr/local/bin/wkhtmltopdf /usr/bin/`<br>
`sudo ln -s /usr/local/bin/wkhtmltoimage /usr/bin`
