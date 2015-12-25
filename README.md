English Version Below

# VAM2(vagrant-ansible-magento2)
Vagrantの自動provisionを利用したMagento2 CEの簡単セットアップ開発環境（CentOS7.1)

ほぼすべてのインストールステップは[公式ドキュメント](http://devdocs.magento.com/guides/v2.0/install-gde/bk-install-guide.html)に準拠しています。


# box配布を開始しました
VAM2で構築したboxを[kzkiq2nd/vam2@Atlas](https://atlas.hashicorp.com/kzkiq2nd/boxes/vam2)で配布開始しました。

Vagrant 1.7.4 が入っていれば以下の手順で起動できます。

__とりあえず動かしたいという方にはboxを利用するのをおすすめします__

```
vagrant box add kzkiq2nd/vam2
vagrant init kzkiq2nd/vam2
vagrant up
```

### 仕様
Magento2 + Sample-Dataのtar.gzインストール版


- CentOS7.1
- PHP5.6
- MariaDB10


- 管理画面URL = `/admin/`
- 管理ユーザー = `admin`
- 管理パスワード = `admin123`


- DBネーム = `magento2_db`
- DBユーザー = `magento2_db_user`
- DBパスワード = `magento2_db_pass`

### 注意
boxサイズが1.3GBほどあり重いのでご注意ください。

## VAM2での起動の注意
VAM2でVMを構築することは可能ですが、tar.gzインストール版とComposerインストール版が混在した状態であり、中を読まれる際はご注意ください。

- 実行する親機（利用しているOSX）にVagrant実行環境および、Ansible実行環境が必要になります。
- また、現時点（2015/11/25）での利用環境はMacのみを想定しています。
- M2公式での実装の変化には緩やかについていきます。詳しくはgithubリリースを参照ください。

## 利用方法
0. 必要な環境を準備する（OSX + Vagrant + Ansible + Virtualbox）
0. 任意のディレクトリに`git clone`。
0. `/provision/group_vars/all.yml.sample`を`/provision/group_vars/all.yml`に変更。
0. `/provision/group_vars/all.yml`の`github_token:`に [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)を追加。※[composer installのAPI制限](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)対策。
0. `all.yml`にてMagento`Secure Keys`を入力します。[magento.comでアカウントを作成し](http://magento.com/)、[MY ACCOUNT] > [Developpers] >
[[Secure Keys](http://www.magentocommerce.com/magento-connect/customerdata/secureKeys/list/)]で`Secure Keys`を生成し、`magento_public_key:`と`magento_private_key:`に入力する.([Magento2-CEのダウンロード認証のため](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce))
0. `vagrant up`

### Magento2`Secure Keys`について
Magento2CEのダウンロードには、開発者向け認証キー・パスが必要になりました。詳しくは[こちら](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)を参照ください。

## 必要要件（以下環境での動作確認済み）
- OSX = 10.10.5
- [vagrant](https://www.vagrantup.com/) = 1.7.4
- [ansible](http://www.ansible.com/) = 1.9.4
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.10

## 構成
- boxcutter/centos71 (virtualbox, 2.0.9)
- PHP 5.6 (from webtatic rpm)
- MariaDB 10.0.22 (from mariadb.org rpm)

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

## NOTICE
You can use [Vagrant Box packed with VAM2 from Atlas](https://atlas.hashicorp.com/kzkiq2nd/boxes/vam2).

```
vagrant box add kzkiq2nd/vam2
vagrant init kzkiq2nd/vam2
vagrant up
```

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
