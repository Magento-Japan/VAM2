# VAM2(vagrant-ansible-magento2)
Magento2β on CentOS7.1 LAMP stack.

## Configuration
0. `git clone`
0. Rename `/provision/group_vars/all.yml.sample` to `/provision/group_vars/all.yml`.
0. Add [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) to `all.yml`.(for [composer install](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens))
0.`vagrant up`

## Stack
- CentOS 7.1(boxcutter/centos71)
- PHP 5.6(from webtatic rpm)
- MariaDB 10.0

## Requirements
- [vagrant](https://www.vagrantup.com/) = 1.7.4
- [ansible](http://www.ansible.com/) = 1.9.2
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.2

## DB info.
- `db name` = `magento2_db`
- `db user name` = `magento2_user`
- `db password(root & magento2_user)` = `password`

## NOTE
http://devdocs.magento.com/guides/v1.0/install-gde/install/composer-clone.html#instgde-prereq-compose-access
