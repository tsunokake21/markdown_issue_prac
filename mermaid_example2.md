## 図の種類
#### フローチャート

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

#### シーケンス図
```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```  

#### ガントチャート
```mermaid
gantt
dateFormat  YYYY-MM-DD
title ガントチャートのサンプル
excludes weekdays 2014-01-10

section A section
完了したタスク            :done,    des1, 2022-07-06,2022-07-08
アクティブなタスク        :active,  des2, 2022-07-09, 3d
未来のタスク              :         des3, after des2, 5d
別な未来のタスク          :         des4, after des3, 5d
```

#### クラス図
```mermaid
Class diagram
classDiagram
Class01 <|-- AveryLongClass : Cool
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 --> C2 : Where am i?
Class09 --* C3
Class09 --|> Class07
Class07 : equals()
Class07 : Object[] elementData
Class01 : size()
Class01 : int chimp
Class01 : int gorilla
Class08 <--> C2: Cool label
```

#### 円グラフ
```mermaid
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

引用元：https://notepm.jp/help/mermaid