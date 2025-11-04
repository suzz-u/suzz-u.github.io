# EconomyShopGUI (Free版) コマンド一覧

このドキュメントは、EconomyShopGUIの**無料版**で利用可能な主要コマンドとパーミッション（権限ノード）をまとめたものです。

**コマンドの前提:**
* メインコマンドは `/economyshopgui` です。
* 多くのコマンドはエイリアス（短縮形）として `/eshop` や `/editshop` を使用できます。

---

## プレイヤー向けコマンド

主にプレイヤーがアイテムの売買に使用するコマンドです。

| コマンド | パーミッション | 説明 |
| :--- | :--- | :--- |
| `/shop` | `EconomyShopGUI.shop` | メインのショップGUIを開きます。 |
| `/shop <カテゴリ名>` | `EconomyShopGUI.shop.<カテゴリ名>` | 指定したカテゴリのショップを直接開きます。 |
| `/sellgui` | `EconomyShopGUI.sellgui` | アイテムを入れて売却できる専用のGUIを開きます。 |
| `/sellall` | `EconomyShopGUI.sellall` | インベントリ内の売却可能なアイテムをすべて売却します。 |
| `/sellall <Material>` | `EconomyShopGUI.sellall.item` | 指定した種類のアイテムをインベントリ内からすべて売却します。 |
| `/sellall hand` | `EconomyShopGUI.sellall.hand` | 現在手に持っているアイテム（1スタックまたは持っている分）を売却します。 |
| `/sellall handall` | `EconomyShopGUI.sellall.handall` | 手に持っているアイテムと同じ種類のアイテムを、インベントリ内からすべて売却します。 |

---

## 管理者向けコマンド (ユーティリティ)

プラグインの管理、リロード、情報確認などに使用するコマンドです。

| コマンド | エイリアス例 | パーミッション | 説明 |
| :--- | :--- | :--- | :--- |
| `/economyshopgui reload` | `/sreload` | `EconomyShopGUI.reload` | すべての設定ファイル（config, shopsなど）をリロードします。 |
| `/economyshopgui version` | `/eshop version` | `EconomyShopGUI.version` | プラグインのバージョン情報を確認します。 |
| `/economyshopgui open <カテゴリ> [プレイヤー名]` | `/eshop open` | `EconomyShopGUI.open` | 指定したプレイヤー（または自分）に、指定したショップカテゴリを強制的に開きます。 |
| `/economyshopgui price <Material>` | `/eshop price` | `EconomyShopGUI.price` | 指定したアイテムの現在のショップ価格（購入/売却）を確認します。 |
| `/economyshopgui import Essentials` | `/eshop import` | `EconomyShopGUI.import` | Essentialsの`worth.yml`からアイテム価格をインポートします。 |
| `/economyshopgui language <言語ファイル名>` | `/eshop lang` | `EconomyShopGUI.language` | プレイヤー自身の表示言語を変更します。（例: `en`, `ja`） |
| `/economyshopgui languages` | `/eshop langs` | `EconomyShopGUI.languages` | 利用可能な言語ファイルの一覧を表示します。 |

---

## 管理者向けコマンド (ショップ編集)

ショップのアイテムやカテゴリ（セクション）を編集するためのコマンドです。

### アイテムの追加・削除

| コマンド | エイリアス例 | パーミッション | 説明 |
| :--- | :--- | :--- | :--- |
| `/editshop addhanditem <カテゴリ> <購入価格> <売却価格>` | `/eshop addhand` | `EconomyShopGUI.eshop.addhanditem` | **手に持っているアイテム**（NBT/エンチャント含む）をショップに追加します。 |
| `/editshop additem <カテゴリ> <Material> <購入価格> <売却価格> [表示名]` | `/eshop additem` | `EconomyShopGUI.eshop.additem` | 指定したMaterial（アイテムID）をショップに基本的なアイテムとして追加します。 |
| `/editshop deleteitem <カテゴリ> <スロット番号>` | `/eshop delitem` | `EconomyShopGUI.eshop.deleteitem` | 指定したカテゴリの、指定したスロット番号にあるアイテムを削除します。 |
| `/editshop setprice <Material> <購入価格> <売却価格>` | `/eshop setprice` | `EconomyShopGUI.eshop.setprice` | （shops.ymlに存在する）指定したアイテムの価格を上書き設定します。 |

### カテゴリ（セクション）の編集

| コマンド | エイリアス例 | パーミッション | 説明 |
| :--- | :--- | :--- | :--- |
| `/editshop addsection <カテゴリ名> <Material> <表示名> <スロット番号>` | `/eshop addsec` | `EconomyShopGUI.eshop.addsection` | メインショップ画面に新しいカテゴリ（セクション）を追加します。 |
| `/editshop delsection <カテゴリ名>` | `/eshop delsec` | `EconomyShopGUI.eshop.deletesection` | 指定したカテゴリを削除します。 |

### 高度な編集（アイテム・カテゴリ共通）

無料版では、主にアイテムやカテゴリの基本的な設定（価格、Material、表示名など）を変更できます。

**基本構文 (アイテム):**
`/editshop edititem <カテゴリ> <スロット番号> <アクション> [キー] [値]`
**パーミッション:** `EconomyShopGUI.eshop.edititem`

**基本構文 (カテゴリ):**
`/editshop editsection <カテゴリ名> <アクション> [キー] [値]`
**パーミッション:** `EconomyShopGUI.eshop.editsection`

**主なアクション (Free版):**
* `set buy <価格>`: 購入価格を設定
* `set sell <価格>`: 売却価格を設定
* `set material <Material>`: アイテム/カテゴリのアイコンを変更
* `set displayname <名前>`: 表示名を変更
* `add lore <説明文>`: 説明文（Lore）の行を追加
* `remove lore <行番号>`: 説明文（Lore）の指定した行を削除