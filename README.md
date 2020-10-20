# rsyncd

![ansible ci](https://github.com/link-u/ansible-roles-v2_rsyncd/workflows/ansible%20ci/badge.svg)

## 概要

rsyncd のインストール, 設定を行う.

## 動作確認バージョン

- Ubuntu 18.04 (bionic)
- ansible >= 2.8
- Jinja2 2.10.3

## 使い方 (ansible)

### Role variables

```yaml
### インストール設定 ###############################################################################
## 基本設定
rsyncd_install_flag: True  # インストールフラグ


### conf ファイル 設定 #############################################################################
## Global オプション
rsyncd_global_uid: root
rsyncd_global_gid: root
rsyncd_global_read_only: no
rsyncd_global_log_file: /var/log/rsyncd.log
rsyncd_global_pid_file: /var/run/rsyncd.pid
rsyncd_global_reverse_lookup: no

## Module オプション
rsyncd_sections: []
# サービスごとの設定例
#rsyncd_sections:
#  - name: comipla
#    path: /usr/src/app/images/comipla/
#    hosts_allow: 192.0.2.0/24
#    hosts_deny: "*"
#    read_only: false
```

### Example playbook

```yaml
- hosts:
    - servers
  roles:
    - { role: rsyncd, tags: ["rsyncd"] }
```

## 後方互換性について

### 削除された変数の一覧

以下の変数は `group_vars` から削除して頂いて大丈夫です.

* `rsyncd_ufw_enabled` と `rsyncd_ufw_allow_from`
  * ufw の設定に関する項目であり, それらは ufw role で実行する方針に切り替えたため削除しました.


## Licence

MIT
