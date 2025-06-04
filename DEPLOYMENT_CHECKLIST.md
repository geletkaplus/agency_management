# Deployment Checklist

## Before First Deployment
- [ ] Update GitHub repository with all changes
- [ ] Set up Digital Ocean droplet (Ubuntu 22.04)
- [ ] Point domain to droplet IP (optional)
- [ ] Add SSH key to droplet

## GitHub Secrets to Add
- [ ] DROPLET_IP - Your droplet's IP address
- [ ] SSH_PRIVATE_KEY - SSH key for deploy user

## On Server Setup
- [ ] Run setup_server.sh script
- [ ] Configure PostgreSQL password
- [ ] Set up .env file with production values
- [ ] Generate new SECRET_KEY
- [ ] Run initial migrations
- [ ] Create superuser
- [ ] Set up SSL certificate (if using domain)

## Security
- [ ] Change all default passwords
- [ ] Enable firewall (ufw)
- [ ] Disable root SSH login
- [ ] Set up regular backups
