# VAM2(vagrant-ansible-magento2)
VagrantとAnsibleを利用した、Magento2のローカル環境構築スクリプトです。

インストール手順は[公式ドキュメント](http://devdocs.magento.com/guides/v2.2/install-gde/prereq/integrator_install.html)に準拠し、
パッケージtypoや日本からのcomposrインストールが重い問題などを回避しています。

### 概要
- Magento2.2.1をローカルに建てます。

#### サーバー基本構成
- CentOS 7.4
- httpd 2.4.6
- php 7.1.11
- mysql 5.7.20

## 動作確認済み環境
- macOS
- [virtualbox](https://www.virtualbox.org/wiki/Downloads) = 5.1.30
- [vagrant](https://www.vagrantup.com/) = 2.0.1
- [ansible](http://www.ansible.com/) = 2.4.2.0

## VAM2起動の注意事項
- Composer Installの失敗回避のため、Vagrantのメモリ利用を2GB設定にしています。

## 利用方法
0. 必要環境（Vagrant + Ansible + Virtualbox）を準備
0. このリポジトリを`git clone`
0. 変数ファイル`/provision/group_vars/all.yml.sample`を`/provision/group_vars/all.yml`に変更
0. 変数ファイル`/provision/group_vars/all.yml`の`github_token:`に [github personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)を追加。※[composer installのAPI制限](https://getcomposer.org/doc/articles/troubleshooting.md#api-rate-limit-and-oauth-tokens)対策。
0. 変数ファイルに`Magento Secure Keys`を追加。[magento.comでアカウントを作成し](http://magento.com/)、[MY ACCOUNT] > [Developpers] >
[[Secure Keys](http://www.magentocommerce.com/magento-connect/customerdata/secureKeys/list/)]で`Secure Keys`を生成し、`magento_public_key:`と`magento_private_key:`にコピペ.([Magento2-CEのcomposer認証のため](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html#integrator-first-composer-ce))
0. [各種変数を任意に変更してください](provision/group_vars/all.yml.sample)
0. `vagrant up`して`http://192.168.33.10/magento2/`にアクセス。

### 補足事項：Magento2`Secure Keys`
Composer経由でのMagento2CEダウンロードには、開発者向け認証キーペアが必要です。

詳しくは[こちら](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)を参照。
