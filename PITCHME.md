# UML勉強会
クラス図とシーケンス図

---

### あじぇんだ
- UMLとは
- クラス図とは
- シーケンス図とは

---

## UMLとは

---

### UMLとは
- **統一モデリング言語** である
  - 主にオブジェクト指向分析や設計のための、記法の統一がはかられたモデリング言語

- つまり何が言いたいかというと |
  - 詳細な設計を残すための手段ではない
  - 情報の不足によって咎められることはない

---

## クラス図とは

---

### クラス図とは
- オブジェクト指向分析・設計の大黒柱
- システムのクラスと、その相互関係
  (継承、集約、関連を含む)を表す

- Tips |
  - クラスの責務を明確にする |
  - クラスが責務にないことをしていないか確認する |
    - 別の役割を担っていないか |

---

### クラスの表現
- クラス図は次の要素で構成される

```uml
@startuml
class クラス名 <<ステレオタイプ（省略可能）>> {
  + 属性（省略可能）
  + 操作（省略可能）()
}
@enduml
```

- 共通表現 |
  - static
    - 属性や操作に下線が引かれる
  - abstract
    - イタリックで表示される（要は斜体）

---

### クラス名

- ステレオタイプ
  - クラスの種別
    - ex. `<<interface>>`
  - 表現する場合、クラス名の上部に記述する

---

### 属性
##### 可視性 名前 : 型 = 初期値 { 制約条件 }
※名前以外は省略可能

- 可視性
  - +public / -private
  - #protected / ~package

```uml
@startuml
class クラス名 {
  + public : string = ""
  - private : integer = 0
  # protected : float[]
  ~ package : double
}
@enduml
```

---

### 操作
##### 可視性 名前 ( 引数の名前 : 引数の型 ) : 戻り値の型
※名前以外は省略可能

- 可視性
  - 属性と同じ

```uml
@startuml
class クラス名 {
  + add(num1:integer, num2:integer) : integer
  - minus(num1:integer) : void
}
@enduml
```

---

### 相互関係
- 線形
  - 継承（汎化）
  - 集約
  - 関連
  - 依存
  - その他（コンポジション、実現）
- 多重度

--- 

### 継承（汎化）
- A は B の一種である
  - is_a の関係を表現する

```uml
@startuml
class Car
class Bus
class Truck

Car <|-- Bus
Car <|-- Truck
@enduml
```

---

### 集約
- A は B の一部である
  - 全体と一部の関係を表現する

```uml
@startuml
class Car
class Wheel
class Handle

Car "1" o-- "4" Wheel
Car "1" o-- "1" Handle
@enduml
```

---

### 関連
- A と B は結びつきがある

```uml
@startuml
class Car
class Maintenance

Car - Maintenance
@enduml
```

---

### 依存
- 相手の状態、もしくはイベントに対して影響を受ける

```uml
@startuml
class Car
class Driver

Car <.. Driver
@enduml
```

---

### 実現
- 相手を具象化する
  - interfaceと同等の意味

```uml
@startuml
class Drive <<interface>>
class Airplane
class Car

Drive <|. Airplane
Drive <|. Car
@enduml
```

---

## シーケンス図とは

---

### シーケンス図とは
- 時間軸に沿ってクラスやオブジェクト間のやりとりを表現する図
- 機能ごとに相互作用（Interaction）と呼ばれるフレーム内に処理内容を記述する

- Tips |
  - 誰が 何を どうするか の手順書
  - 全体や一部の流れを確認する

---

### シーケンスの構成要素
- ライフライン
  - 使用するオブジェクトやクラスを表現する
- 実行仕様
  - 実行状態であることを意味する
- 停止
  - ライフライン自体の消滅を意味する
- メッセージ
  - 同期
  - 非同期
  - 応答
  - ファウンド
  - ロスト

---

### シーケンスの構成要素（図解）
```uml
@startuml
class Switch
class MngServer

MngServer -> Switch : Login（同期）
MngServer <-- Switch : （同期）


MngServer <<- Switch : SNMPTrap
MngServer -> MngServer : Handle
MngServer -> Switch : CLI
@enduml
```

---

### シーケンスの制御構造
- 複合フラグメント
  - alt
    - 分岐処理
    - if ~ else ~
  - opt
    - 条件を満たした時に実行される処理
    - if
  - loop
    - 繰り返し処理
  - 他
    - par / ref / break
    - critical / assert / neg
    - ignore / consider

---

## まとめ

---

### まとめ
- UMLは難しい！
  - 構成する要素が多すぎる！
  - そこまで詳細に書けない！

---

### まとめ
- 今回の勉強会の目的 |
  - 意識の擦り合わせや振り返りの材料としてUMLを使おう
  - 自分の知識という資産を増やそう

---

### まとめ
- クラス図
  - 重要な属性や操作を書き出し、責務や役割を確認する
  - 関連を整理して名前と立場が一致しているか確認する

- シーケンス図 |
  - 処理の流れを書き出し、意識を擦り合わせる
    - ロジックの考慮漏れを発見する
    - パフォーマンスへの影響を発見する
  - クラス図の関連を振り返る |
  
---

### ご静聴ありがとうございました
