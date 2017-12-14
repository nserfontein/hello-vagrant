# Installation
```bash
vagrant up
```

# Once-off:
```bash
cd /www/myProject
# TODO: permission denied here:
chown -R 777 storage/
```

# Confirm
```bash
vagrant ssh
cat /etc/apache2/sites-available/000-default.conf

cd /var/www
ls -ld

cat myProject/config/database.php
```

# Notes:
- Chef script for demonstration purposes only
- Needs more work, eg. safe passwords

# TODO:
- Getting permission denied error on storage