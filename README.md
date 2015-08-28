# VAM2JP(vagrant-ansible-magento2-jp)
Vagrantを利用した日本語版`Magento2β`開発環境〜季節のCentOS7+PHP5.6を添えて〜

## Configuration
`vagrant up`

## Requirements
- `vagrant >= 1.7.4`
- `Ansible >= 1.9.2`
- `virtualbox` >= 5.0.2`

## DB
- `db name` = `magento2_db`
- `db user name` = `magento2_user`
- `db password(root,magento2_user)` = `password`

## Note
- Magento2初期設定と日本語データのデプロイが未完
- boxは`boxcutter/centos71`を利用している
- 専用boxを用意するつもりがある（Pack時のコードも残せばいいかな）
- 冪等性...
