# 作業履歴(WORKHISTORY.md)

## ディレクトリ構造適正化 0000
    2014-02-17
    "ディレクトリ構造適正化(新規) 0000"
    不要ファイル削除sample.db テスト用dbにつき

## 資料の整備 0001
    2014-02-17
    "資料の整備(新規) 0001"
    作業履歴 WORKHISTORY.mdを新設
    Markdown形式にて履歴保存、gitコミットの詳細を記録

    2014-02-22
    "資料の整備(README.md) 0001"
    README.mdを更新

## [Manager]管理者向け機能 0002
    2014-02-17
    要件
    ・yoyakkuシステムにならい開発管理者向けの機能、画面作成
    ・命名 Manager
    ・開発中に付きログイン機能なしで実装
    ・サイトの画面構成を一覧できるリスト作成 manager/list
    ・dbの生データを直接回覧修正できる画面 manager/myadmin
    ・現在のPreviewは廃止削除

    "[Manager]管理者向け機能(新規) 0002"
    基本要件を定義

    "[Manager]管理者向け機能(Manager追加) 0002"
    Managerひな形追加

## [AddressBook]ルート見直し 0003
    2014-02-18
    "[AddressBook]ルート見直し(不要箇所削除) 0003"
    不要コメントアウト、インデント体裁の修正

## [Auth]ログイン機能 0004
    2014-02-22
    要件
    ・画面ヘッダー部分の右上にログインをクリックする個所をもうける
    ・クリックするとログイン入力出来る画面に遷移する
    ・ログインした状態ではログイン名が表示される
    ・ログイン名をクリックするとログアウト
    ・基本的にどこの画面でもヘッダーの右上にログインが見れるようにする

    ・ログイン機能 lib/AddressBook/Auth.pm
        ・ルート /auth/login
            ・Auth.pmのsub login {}を実行
            ・dbのadminテーブルに存在確認
            ・認証が許可 セッションに書き込み 画面トップに遷移
            ・認証に失敗 ログイン画面表示
        ・ルート /auth/logout
            ・Auth.pmのsub logout {}を実行
            ・セッションを破棄して画面トップに遷移 専用画面なし

    ・ログイン画面 templates/auth/login.html.ep
        ・入力フォーム
            メールアドレス、パスワード
        ・フォーム実行ボタン
            ログイン
    ・ログイン画面デザイン public/css/contents/auth.css
        ・共通
            import.css (読み込み設定)
            reset.css (初期値)
            structure (基本レイアウト)
            header.css (ヘッダー部分)
            footer.css (フッター部分)
    ・ログイン画面動的なデザイン public/js/auth/login.js

    "[Auth]ログイン機能(新規) 0004"
    基本要件を定義

    "[Auth]ログイン機能(ルート記述変更) 0004"
    login を auth/login  logout を auth/logout に変更

    "[Auth]ログイン機能(FormValidator::Lite) 0004"
    バリデート機能実装のため
    FormValidator::Lite インストール carton install

    "[Auth]ログイン機能(バリデート原型) 0004"
    バリデートの原型、postリクエストのみに対応

    "[Auth]ログイン機能(HTML::FillInForm) 0004"
    フィルイン機能実装のため
    HTML::FillInForm インストール carton install

    "[Auth]ログイン機能(API/Auth.pm実装) 0004"
    フィルイン機能実装
    バリデート機能改訂(エラーメッセージ表示)

    "[Auth]ログイン機能(HTML,CSS/改訂) 0004"
    ヘッダーナビ表示位置調整
    ログイン時に「さん」をつける
    エラーメッセージを強調

## [Setting]設定機能 0005
    2014-03-15
    要件
    ・各種機能を設定する機能を新設
    ・アカウント管理(新規 変更 削除 表示)
    ・プロフィール管理(新規 変更 削除 表示)

    ・設定機能 lib/AddressBook/Setting.pm
        ・ルート /setting/account_edit
        ・ルート /setting/account_search

        ・ルート /setting/profile_edit
        ・ルート /setting/profile_search

    ・アカウント画面
        templates/setting/account_edit.html.ep
        templates/setting/account_search.html.ep

    ・プロフィール画面
        templates/setting/profile_edit.html.ep
        templates/setting/profile_search.html.ep

    ・設定画面デザイン public/css/contents/setting.css
    ・共通
        import.css (読み込み設定)
        reset.css (初期値)
        structure (基本レイアウト)
        header.css (ヘッダー部分)
        footer.css (フッター部分)

    ・アカウント画面動的なデザイン public/js/setting/account.js
    ・プロフィール画面動的なデザイン public/js/setting/profile.js

    "[Setting]設定機能(新規) 0005"
    基本要件と各種ファイル準備

    "[Setting]設定機能(API/account_search 新規) 0005"
    最低限の検索条件にて暫定作成
