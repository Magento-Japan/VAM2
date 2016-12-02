# VAM2(vagrant-ansible-magento2)
VagrantとAnsibleを利用したMagento2.1の開発環境構築スクリプトです。

インストール手順は[公式ドキュメント](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html)にほぼ準拠し
ドキュメントのtypo等回避していますが、CentOS7とPHP7においての`libicu問題`の回避方法は現在調査中です。（PHP7でpecl/intlがmake faildしてしまう）

なお、intl拡張との相性問題は[ベリテワークスさんのブログ](https://principle-works.jp/blog/magento2-setup-guide-2016-edition)にまとまっています。

### 仕様
- Composer経由インストール式のMagento2.1.2クリーンインストール
- サンプルデータ投入まで（日本語化・自動cronは未設定）

#### 基本構成
- bento/centos-7.2 (virtualbox, 5.1.10)
- CentOS 7.2
- PHP 7.0
- MySQL 5.7

## 動作確認環境
- OSX = 10.12.1
- [vagrant](https://www.vagrantup.com/) = 1.8.4
- [ansible](http://www.ansible.com/) = 2.1.0
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.0.10

#### 管理画面
- 管理画面URL = `/admin/`
- 管理ユーザー = `admin`
- 管理パスワード = `admin123`

## DB情報
- `db name` = `magento2_db`
- `db user` = `magento2_user`
- `db password` = `Magento2_db_pass!`
- `db root password` = `Passw0rd!Passw0rd!`

## VAM2での起動の注意
- 相当にメモリーを食うためスペックに余裕のあるラップトップを利用した方がよい。
- VagrantとAnsibleが必要。
- 動作確認済みはMacのみ。

## 利用方法
0. 必要環境を用意する（OSX + Vagrant + Ansible + Virtualbox）
0. 任意のディレクトリにこのリポジトリを`git clone`。
0. 変数ファイル`/provision/group_vars/all.yml.sample`を`/provision/group_vars/all.yml`に変更。
0. 変数ファイルに`/provision/group_vars/all.yml`の`github_token:`に [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)を追加。※[composer installのAPI制限](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)対策。
0. 変数ファイルに`Magento Secure Keys`を追加。[magento.comでアカウントを作成し](http://magento.com/)、[MY ACCOUNT] > [Developpers] >
[[Secure Keys](http://www.magentocommerce.com/magento-connect/customerdata/secureKeys/list/)]で`Secure Keys`を生成し、`magento_public_key:`と`magento_private_key:`に入力する.([Magento2-CEのcomposer認証のため](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce))
0. `vagrant up`して`http://192.168.33.10/magento2/`にアクセス。

### Magento2`Secure Keys`について
Composer経由でのMagento2CEダウンロードには開発者向け認証キー・パスが必要です。

詳しくは[こちら](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)を参照してください。

## 管理情報
- フロントURI = `http://192.168.33.10/magento2/`
- 管理画面URI = `http://192.168.33.10/magento2/admin/`
- 管理ユーザーID = `admin`
- 管理ユーザーパス = `admin123`

[Show all variables](provision/group_vars/all.yml.sample)

## 備考
[Magento2クイックセットアップドキュメント](http://devdocs.magento.com/guides/v2.0/install-gde/install-quick-ref.html)
