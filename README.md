# alt
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
# opt
```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋

    opt 辛いもの好き
        cook ->> kitchenware1: チリペッパーを入れる
    end

```
# par
```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋
    par 処理1
        cook->>kitchenware1: 調味料を入れる
    and 処理2
        cook->>kitchenware1: 水を入れて混ぜる
    end

```
# loop & break

```mermaid
sequenceDiagram
    participant cook as シェフ
    participant kitchenware1 as 鍋

    cook ->> kitchenware1: カレーを煮込む
    loop ときどき
        cook ->> kitchenware1: 混ぜる
        break カレーが煮込まったら
            kitchenware1 -->> cook: 
            note right of cook: ループから脱出
        end
    end

```

|  結合フラグメント   |  正式名称   |   表現内容  |
| --- | --- | --- |
|alt   |  alternative   |  分岐処理   |
|opt	|option|	実行の可否の選択|
|loop|	option|	繰り返し|
|break|	break|	処理の中断|
|par|	parallel|	並行|
|seq|	weak sequencing|	同じライフラインから送信されるメッセージの順序を保証|
|strict	|strict sequencing|	全てのライフラインから送信されるメッセージの順序を保証|
|critical|	critical region|	クリティカル領域(セクション)|
|ignore|	ignore	|実行時に無視されるメッセージの指定|
|consider|	consider|	ignoreの逆|
|neg|	negative|	無効な領域|
|assert|assert	|メッセージ実行後に成立するべき条件の指定|

# 練習

```mermaid
sequenceDiagram
    participant waiter as ウェイター
    participant cook as 料理人

    waiter -) cook : オーダー
    opt からあげの場合
        cook ->> cook: 油を温める
    end
    cook ->> cook: 料理を作る
    cook -->> waiter: 料理

```