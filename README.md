English Version Below

# VAM2(vagrant-ansible-magento2)
Magento2 CEの簡単セットアップ開発環境（CentOS7.1)

ほぼすべてのステップは[公式ドキュメント](http://devdocs.magento.com/guides/v2.0/install-gde/bk-install-guide.html)に準拠しています。

## 利用方法
0. 任意のディレクトリに`git clone`。
0. `/provision/group_vars/all.yml.sample`を`/provision/group_vars/all.yml`に変更。
0. `/provision/group_vars/all.yml`の`github_token:`に [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)を追加。※[composer installのAPI制限](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)対策。
0. おなじく、`all.yml`にて。[magento.comでアカウントを作成し](http://magento.com/)、アカウントネームとパスワードを `magento_account_name:`と`magento_account_pass:`に入力する.([Magento2-CEのダウンロード認証のため](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce))
0. `vagrant up`

## 構成
- boxcutter/centos71 (virtualbox, 2.0.8)
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
Magento2 CE on CentOS7.1 LAMP stack.

Almost all the steps of deploy is based on [Developer Documentation(2.0)](http://devdocs.magento.com/guides/v2.0/install-gde/bk-install-guide.html).

## Configuration
0. `git clone`
0. Rename `/provision/group_vars/all.yml.sample` to `/provision/group_vars/all.yml`.
0. Add [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) to `github_token:` on `/provision/group_vars/all.yml`.(for [composer install API rate limit](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens) )
0. Add [magento.com account id and pass](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce)to `magento_account_name`,`magento_account_pass`.(for [download magento2-CE](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce))
0.`vagrant up`

## Stack
- boxcutter/centos71 (virtualbox, 2.0.8)
- PHP 5.6 (from webtatic rpm)
- MariaDB 10.0.22 (from mariadb.org rpm)

## Requirements
- [vagrant](https://www.vagrantup.com/) = 1.7.4
- [ansible](http://www.ansible.com/) = 1.9.4
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.10

## DB info.
- `db name` = `magento2_db`
- `db user name` = `magento2_user`
- `db password(root & magento2_user)` = `password`

## Site information
- front URI = `[Vagrant URL]/magento2/`
- admin URI = `[Vagrant URL]/magento2/admin/`
- admin user name = `admin`
- admin user pass = `admin123`

[Show all variables](provision/group_vars/all.yml.sample)

## Timezone
Comment out [change-timezone-ja task](provision/roles/change-timezone-ja/) on [playbook](provision/playbook.yml).

## NOTE
[Installation quick reference (tutorial)](http://devdocs.magento.com/guides/v2.0/install-gde/install-quick-ref.html)
