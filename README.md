# gitlab-docker

install docker
install docker compose

docker pull gitlab/gitlab-ce

docker-compose up -d

install nginx

ssl domain

# firewall

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F
iptables -X
iptables -t filter -A INPUT -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -t filter -A OUTPUT -p tcp -m tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT

# backup

gitlab-rake gitlab:backup:create 

# restore

gitlab-ctl stop unicorn

gitlab-ctl stop sidekiq

gitlab-ctl stop

gitlab-rake gitlab:backup:restore BACKUP=123....123 (/var/opt/gitlab/backups/123....123_gitlab....tar)

gitlab-ctl start

# Error
Backup and restore same version gitlab

Error CICD => reset token runner on db 

