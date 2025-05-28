# 🛠 Troubleshooting Guide

## ❌ Can't Access Nextcloud via Browser

- Make sure NGINX Proxy Manager is properly pointing to port 8080
- Confirm ports 80/443 are forwarded in your router
- Verify your domain is resolving to your public IP address

## 🔒 Trusted Domain Error

You might see a message like:

```
Access through untrusted domain
```

To fix:

```bash
docker exec -it nextcloud bash
vi /var/www/html/config/config.php
```

Add or update the trusted_domains array:

```php
'trusted_domains' => [
  0 => 'localhost',
  1 => 'nextcloud.yourdomain.com',
],
```

## 🐳 Fixing File Permission Issues

If uploads fail or files can't be accessed, try resetting permissions:

```bash
sudo chown -R www-data:www-data ./nextcloud_data
sudo chmod -R 755 ./nextcloud_data
```

Or inside the container:

```bash
docker exec -it nextcloud bash
chown -R www-data:www-data /var/www/html
```

## 🐘 Database Connection Issues

If logs show something like:

```
SQLSTATE[HY000] [1045] Access denied for user
```

Check that:
- Your `.env` values match the Docker Compose settings
- The MariaDB container is healthy and running

Restart everything:

```bash
docker compose down
docker compose up -d
```

## 🔁 Restart the Stack

If all else fails:

```bash
docker compose down
docker compose up -d
```

## 🧠 Monitor with Portainer

- Use **Portainer** at `http://<your-ip>:9000`
- Navigate to **Containers > nextcloud > Logs**
- Look for startup errors, permission problems, and network issues
