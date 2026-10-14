# DV-Judge-bruno

DV-Judge のバックエンド API を手動で試すための [Bruno](https://www.usebruno.com/) コレクションです。
システム全体の構成は [DV-Judge (Umbrella リポジトリ)](https://github.com/dWork003/DV-Judge) を参照してください。

## 使い方

1. Bruno でこのフォルダを開く (Open Collection)
2. 右上の環境選択で `Develop` を選ぶ
3. 環境変数 `userPassword` (シークレット) に自分のパスワードを設定する
4. `Authentication/Login` を実行してから、他の API を実行する
   (ログインで発行された cookie が以降のリクエストに自動で付与されます)

## 環境変数 (`environments/Develop.yml`)

| 変数名           | 内容                                     |
| ---------------- | ---------------------------------------- |
| `baseURL`        | バックエンドの URL (`http://localhost:8000`) |
| `userEmployeeId` | ログインに使う社員番号                   |
| `userPassword`   | ログインに使うパスワード (シークレット。git には保存されない) |

## リクエスト一覧

| フォルダ         | リクエスト | 内容                                   |
| ---------------- | ---------- | -------------------------------------- |
| `Authentication` | `Login`    | `POST /api/login` ログイン             |
|                  | `Profile`  | `GET /api/profile` ログイン中のユーザー |
|                  | `Logout`   | `GET /api/logout` ログアウト           |
| `Topics`         | `ListTopics`  | `GET /api/topics` 議題の一覧        |
|                  | `CreateTopic` | `POST /api/topics` 議題の投稿       |
| `Admin` (管理者のみ) | `ListAdmins` | `GET /api/admin/admins` 管理者の一覧 |
|                  | `AddAdmin`    | `POST /api/admin/admins` 管理者の追加 |
|                  | `RemoveAdmin` | `DELETE /api/admin/admins/{社員番号}` 管理者から外す |
|                  | `SearchEmployees` | `GET /api/admin/employees?keyword=` 社員検索 |

API を追加したら、対応するリクエストをここに追加し、レスポンス例 (`examples`) も保存してください。
