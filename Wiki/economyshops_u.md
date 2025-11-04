# EconomyShopGUI (Premium) コマンド大全

このドキュメントは、Minecraftプラグイン「EconomyShopGUI」の主要なコマンドとパーミッション（権限ノード）を網羅的にまとめたものです。

**コマンドの前提:**
* メインコマンドは `/economyshopgui` です。
* 多くのコマンドはエイリアス（短縮形）として `/eshop` や `/shopadmin` を使用できます。
* ショップ編集関連のコマンドは `/editshop` でも実行できる場合があります。

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
| `/economyshopgui version` | `/eshop version` | `EconomyShopGUI.version` | プラグインの現在のバージョンと最新バージョンを確認します。 |
| `/economyshopgui open <カテゴリ> [プレイヤー名]` | `/eshop open` | `EconomyShopGUI.open` | 指定したプレイヤー（または自分）に、指定したショップカテゴリを強制的に開きます。 |
| `/economyshopgui price <Material>` | `/eshop price` | `EconomyShopGUI.price` | 指定したアイテムの現在のショップ価格（購入/売却）を確認します。 |
| `/economyshopgui import Essentials` | `/eshop import` | `EconomyShopGUI.import` | Essentialsの`worth.yml`からアイテム価格をインポートします。 |
| `/economyshopgui language <言語ファイル名>` | `/eshop lang` | `EconomyShopGUI.language` | プレイヤー自身の表示言語を変更します。（例: `en`, `ja`） |
| `/economyshopgui languages` | `/eshop langs` | `EconomyShopGUI.languages` | 利用可能な言語ファイルの一覧を表示します。 |

---

## 管理者向けコマンド (ショップ編集 - アイテム)

ショップ内のアイテムを追加、編集、削除するためのコマンドです。

| コマンド | エイリアス例 | パーミッション | 説明 |
| :--- | :--- | :--- | :--- |
| `/editshop addhanditem <カテゴリ> <購入価格> <売却価格>` | `/eshop addhand` | `EconomyShopGUI.eshop.addhanditem` | **手に持っているアイテム**（NBT/エンチャント含む）をショップに追加します。 |
| `/editshop additem <カテゴリ> <Material> <購入価格> <売却価格> [表示名]` | `/eshop additem` | `EconomyShopGUI.eshop.additem` | 指定したMaterial（アイテムID）をショップに基本的なアイテムとして追加します。 |
| `/editshop deleteitem <カテゴリ> <スロット番号>` | `/eshop delitem` | `EconomyShopGUI.eshop.deleteitem` | 指定したカテゴリの、指定したスロット番号にあるアイテムを削除します。 |
| `/editshop setprice <Material> <購入価格> <売却価格>` | `/eshop setprice` | `EconomyShopGUI.eshop.setprice` | （shops.ymlに存在する）指定したアイテムの価格を上書き設定します。 |

---

### 高度なアイテム編集 (`/editshop edititem`)

既存のアイテム設定を細かく変更します。

**基本構文:** `/editshop edititem <カテゴリ> <スロット番号> <アクション> [キー] [値]`
**パーミッション:** `EconomyShopGUI.eshop.edititem`

| アクション | キー / 値 | 説明 (使用例) |
| :--- | :--- | :--- |
| `set` | `<buy \| sell \| material> <値>` | アイテムの基本設定を変更します。<br>例: `/... set buy 100` (購入価格を100に) <br>例: `/... set material STONE` (アイテムを石に) |
| `add` | `<enchantments \| lore> <値>` | エンチャントや説明文（Lore）を追加します。<br>例: `/... add enchantments sharpness:5` (鋭さVを追加)<br>例: `/... add lore "これはテストです"` |
| `remove` | `<enchantments \| lore> <値>` | エンチャントや説明文（Lore）を削除します。<br>例: `/... remove enchantments sharpness` (鋭さを削除) |
| `set` | `command <コマンド>` | (Premium版) アイテム購入時に実行するコマンドを設定します。 |
| `set` | `permission <ノード>` | (Premium版) アイテムの表示/購入に必要な権限ノードを設定します。 |

---

## 管理者向けコマンド (ショップ編集 - カテゴリ)

ショップのメインページ（カテゴリ）を編集するためのコマンドです。

| コマンド | エイリアス例 | パーミッション | 説明 |
| :--- | :--- | :--- | :--- |
| `/editshop addsection <カテゴリ名> <Material> <表示名> <スロット番号>` | `/eshop addsec` | `EconomyShopGUI.eshop.addsection` | メインショップ画面に新しいカテゴリ（セクション）を追加します。 |
| `/editshop delsection <カテゴリ名>` | `/eshop delsec` | `EconomyShopGUI.eshop.deletesection` | 指定したカテゴリを削除します。 |
| `/editshop editsection <カテゴリ名> <アクション> <キー> <値>` | `/eshop editsec` | `EconomyShopGUI.eshop.editsection` | 既存のカテゴリの設定を変更します。（`edititem`と同様の構文）<br>例: `/... set displayname "§c§lレアアイテム"` (表示名を変更) |

---

## ShopStands モジュール (Premium)

Premium版で利用可能な、物理的なショップスタンド（NPCやアーマースタンド型ショップ）を管理するコマンドです。

| コマンド | パーミッション | 説明 |
| :--- | :--- | :--- |
| `/eshop shopstands give <タイプ> <カテゴリ> [アイテムスロット]` | `eshop.shopstands.give` | ショップスタンドを設置するためのアイテムを取得します。 |
| `/eshop shopstands destroy <ID>` | `eshop.shopstands.destroy` | IDを指定して、設置済みのショップスタンドを強制的に削除します。 |
| `/eshop shopstands browse` | `eshop.shopstands.browse` | 設置されているショップスタンドの一覧をGUIで開きます。 |