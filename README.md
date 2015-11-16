# VAM2(vagrant-ansible-magento2)
Magento2-RC2の簡単セットアップ開発環境（CentOS7.1)

## 利用方法
0. 任意のディレクトリに`git clone`。
0. `/provision/group_vars/all.yml.sample`を`/provision/group_vars/all.yml`に変更。
0. `/provision/group_vars/all.yml`の`github_token:`に [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)を追加。※[composer install](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)のAPI制限対策。
0. `vagrant up`

## 構成
- boxcutter/centos71 (virtualbox, 2.0.7)
- PHP 5.6 (from webtatic rpm)
- MariaDB 10.0.22 (from mariadb.org rpm)

## 必要要件（以下環境での動作確認済み）
- [vagrant](https://www.vagrantup.com/) = 1.7.4
- [ansible](http://www.ansible.com/) = 1.9.4
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.10

## DB情報
- `db name` = `magento2_db`
- `db user name` = `magento2_user`
- `db password(root & magento2_user)` = `password`

## その他情報
- フロントURI = `[Vagrant URL]/magento2/`
- 管理画面URI = `[Vagrant URL]/magento2/admin/`
- 管理ユーザー = `admin`
- 管理ユーザーパス = `admin123`

[Show all variables](provision/group_vars/all.yml.sample)

## 備考
[Magento2クイックセットアップドキュメント](http://devdocs.magento.com/guides/v2.0/install-gde/install-quick-ref.html)

# (EN) VAM2(vagrant-ansible-magento2)
Magento2β on CentOS7.1 LAMP stack.

## Configuration
0. `git clone`
0. Rename `/provision/group_vars/all.yml.sample` to `/provision/group_vars/all.yml`.
0. Add [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) to `github_token:` on `/provision/group_vars/all.yml`.(for [composer install](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens) API rate limit)
0.`vagrant up`

## Stack
- boxcutter/centos71 (virtualbox, 2.0.7)
- PHP 5.6(from webtatic rpm)
- MariaDB 10.0.22(from mariadb.org rpm)

## Requirements
- [vagrant](https://www.vagrantup.com/) = 1.7.4
- [ansible](http://www.ansible.com/) = 1.9.4
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.10

## DB info.
- `db name` = `magento2_db`
- `db user name` = `magento2_user`
- `db password(root & magento2_user)` = `password`

## NOTE
[Installation quick reference (tutorial)](http://devdocs.magento.com/guides/v2.0/install-gde/install-quick-ref.html)
