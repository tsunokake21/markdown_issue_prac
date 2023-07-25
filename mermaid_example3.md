## mermaidで記述できるダイアグラムのチュートリアル

### シーケンス図

#### 基本の書き方
```mermaid
sequenceDiagram
    コック ->> フライパン: ハンバーグを焼く
    フライパン -->> コック : 焼き上がり
```

ただし、この書き方だとライフラインの名前「コック」を「シェフ」に変えたいと思った場合、2箇所直さないといけません。
そこで、ライフラインはエイリアス(別名)をつけておいた方がいいです。

**participant cook as コック**
という書き方でcookというライフラインに「コック」という別名(ラベル)を与えることができます。
これで「コック」を「シェフ」や「板前」に変えたいと思ったら、この行を修正するだけで済みます。

ライフラインにはなるべく抽象的な名前をつけておきましょう。
```mermaid
sequenceDiagram
participant cook as コック
participant kitchenware1 as フライパン
    cook ->> kitchenware1: ハンバーグを焼く
    kitchenware1 -->> cook : 焼き上がり

```

#### 実行仕様
ライフライン上に実行仕様をつけたい場合は、開始と終了の矢印の後に+と-をつけます。
```mermaid
sequenceDiagram
participant cook as コック
participant kitchenware1 as フライパン
    cook ->>+ kitchenware1: ハンバーグを焼く
    kitchenware1 -->>- cook : 焼き上がり

```
実行仕様は入れ子にすることもできます。
```mermaid
sequenceDiagram
participant cook as コック
participant kitchenware1 as フライパン
    cook ->>+ kitchenware1: ハンバーグを焼く
    cook ->>+ kitchenware1: 蓋をする
    kitchenware1 -->>- cook: ふっくら
    kitchenware1 -->>- cook : 焼き上がり

```

#### ノート
シーケンス図にノート(メモ)をつけることもできます。

ノートをつける位置によって、少し指定の仕方が変わります。

|**ノートの位置**|**コード**|
| ライフラインの上 | Note over ライフライン: ノートの内容 |
| ライフラインの右 | Note right of ライフライン: ノートの内容|
| ライフラインの左 | Note left of ライフライン: ノートの内容 |

```mermaid
sequenceDiagram
    participant cook as コック
    participant kitchenware1 as フライパン

    cook ->>+ kitchenware1: ハンバーグを焼く
    Note over kitchenware1: 8分ほど待つ
    kitchenware1 -->>- cook: 焼き上がり
    Note right of kitchenware1: 竹串を刺して透明な汁が出たら完成
```

ライフラインを,(コンマ)でつなげて指定すれば、複数のライフライン上にまたがったノートを書くこともできます。

```mermaid
sequenceDiagram
    participant cook as コック
    participant kitchenware1 as フライパン

    cook ->>+ kitchenware1: ハンバーグを焼く
    Note over cook, kitchenware1: 8分ほど待つ
    kitchenware1 -->>- cook: 焼き上がり

```

#### 複合フラグメント
シーケンスにはループや条件分岐がつきものです。
もちろんmermaidでも表現することができます。

#### 条件分岐(alt)
下記のようにalt～else～endを使って書きます。
alt 条件1
    処理1
else 条件2
    処理2
end

```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋

    alt ビーフカレー
        cook ->> kitchenware1:牛肉を入れる
    else チキンカレー
        cook ->> kitchenware1:鶏肉を入れる
    end

```

#### 条件指定(opt)
opt 条件
    処理
end

```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋

    opt 辛いもの好き
        cook ->> kitchenware1: チリペッパーを入れる
    end

```

#### ループ(loop)
loop 条件
    処理
end

```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋

    cook ->> kitchenware1: カレーを煮込む
    loop ときどき
        cook ->> kitchenware1: 混ぜる
    end

```

#### 背景色
rect rgba(r, g, b, a)
    ....
end

背景色をつけたい部分をrect rgba()～endでくくります。
rgba()で「赤(red)」「緑(green)」「青(blue)」「透過度(alpha)」をそれぞれ指定します。

```mermaid
sequenceDiagram
    participant cook as コック
    participant kitchenware1 as 鍋

    cook ->> kitchenware1: ひき肉を炒める

    rect rgba(255, 0, 255, 0.2)
    opt 辛いもの好き
        cook ->> kitchenware1: 豆板醤を入れる
    end
    end

```

#### コメント
mermaidブロックの中にコメント文を書きたいときは %% これはコメントです のようにします

```mermaid
sequenceDiagram
    コック ->> フライパン: ハンバーグを焼く
    フライパン -->> コック : 焼き上がり
    %% これはコメントなので表示されません

```
