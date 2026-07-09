# MaterialModule

## 1. 基本情報
モジュール名: MaterialModule\
バージョン: v0.1.0 (Draft)\
担当者: (編集で記載)\
作成日: (編集で記載)

## 2. 所属システム

所属システム:\
InfinityMax:GameEngine

上位システム:\
ゲームエンジン

関連モジュール:
* PhysicsModule
* ElectricModule
* MagicModule
* DataModule
* RegistryModule

## 3. モジュール概要
MaterialModuleは、InfinityMax世界に存在する全ての物質・素材の基本情報を管理する基盤モジュールである。\
物質の物理的・化学的・電気的・魔術的性質をデータとして保持し、他モジュールへ提供する。\
本モジュールは、工業、建築、戦闘、魔術、環境システムなど、物質を扱う全てのシステムから利用される。

担当範囲:
* 物質情報管理
* 材料特性管理
* 元素情報管理
* 合金情報管理
* 状態管理
* 性質取得API提供
* 材料比較
* 材料分類

担当しない:
* 物理計算
* 電気計算
* 魔術計算
* アイテム登録

## 4. 設計思想
* 全ての物質情報を統一管理する。
* 物質はデータとして定義する。
* 現実科学を基準にしつつ、InfinityMax独自物質にも対応する。
* 他モジュールはMaterialModuleから物質情報を取得する。
* 新しい物質追加を容易にする。
* 合金・複合材料への拡張を可能にする。

## 5. 機能一覧
MaterialDatabaseSystem
→ 全物質データを管理するデータベース\
ElementSystem
→ 元素情報を管理する\
例:
* 鉄
* 炭素
* マジカニウム

CompoundSystem
→ 化合物を管理する\
例:
* 水
* 酸化鉄

AlloySystem\
→ 合金情報を管理する

例:
* 鋼
* チタン合金

PhysicalPropertySystem
→ 物理的性質を管理する\
管理:
* 密度
* 硬度
* 融点
* 沸点

ThermalPropertySystem
→ 熱特性を管理する\
管理:
* 比熱
* 熱伝導率
* 熱膨張率

ElectricalPropertySystem
→ 電気特性を管理する\
管理:
* 電気抵抗率
* 導電率


MechanicalPropertySystem
→ 機械的性質を管理する\
管理:
* 強度
* 靭性
* 硬度
* 弾性

ChemicalPropertySystem
→ 化学的性質を管理する\
管理:
* 反応性
* 酸化性
* 可燃性

MaterialStateSystem
→ 物質状態を管理する\
状態:
* 固体
* 液体
* 気体
* プラズマ

MagicPropertySystem
→ 魔術的性質を管理する\
管理:
* 魔力保持量
* 魔力伝導率
* 魔術耐性

## 6. 他モジュールとの連携
利用\
**PhysicsModule**
使用内容:
* 密度
* 比熱
* 融点
* 熱伝導率

**ElectricModule**
使用内容:
* 導電率
* 抵抗率

**MagicModule**
使用内容:
* 魔力保持量
* 魔力伝導率

**DataModule**
使用内容:
* 物質データ保存

## 7. データ

基本情報
* MaterialID
* MaterialName
* MaterialType
* ElementNumber
* ChemicalSymbol

物理情報
* Density（密度）
* Mass（質量）
* Volume（体積）
* State（状態）
* MeltingPoint（融点）
* BoilingPoint（沸点）

熱情報
* SpecificHeat（比熱）
* ThermalConductivity（熱伝導率）
* ThermalExpansion（熱膨張率）

機械情報
* Hardness（硬度）
* Strength（強度）
* Toughness（靭性）
* Elasticity（弾性）
* Durability（耐久性）

電気情報
* ElectricalResistance（電気抵抗）
* Conductivity（導電率）
* DielectricConstant（誘電率）

化学情報
* Reactivity（反応性）
* Flammability（可燃性）
* OxidationResistance（酸化耐性）
* CorrosionResistance（腐食耐性）

魔術情報
* MagicCapacity（魔力保持量）
* MagicConductivity（魔力伝導率）
* MagicResistance（魔力抵抗）
* MagicAffinity（魔術適性）


構造情報
* Composition（構成元素）
* AlloyData（合金情報）
* Purity（純度）

## 8. API・公開関数
```
// ===== 基本情報 =====
getMaterial()                 // 指定した物質データを取得する
registerMaterial()            // 新しい物質を登録する
removeMaterial()              // 物質登録を削除する
hasMaterial()                 // 指定物質が存在するか確認する
// ===== 元素 =====
getElementNumber()             // 元素番号を取得する
getChemicalSymbol()            // 元素記号を取得する
// ===== 物理特性 =====
getDensity()                   // 密度を取得する
getMeltingPoint()              // 融点を取得する
getBoilingPoint()              // 沸点を取得する
getMaterialState()             // 物質状態を取得する
// ===== 熱特性 =====
getSpecificHeat()              // 比熱を取得する
getThermalConductivity()       // 熱伝導率を取得する
getThermalExpansion()          // 熱膨張率を取得する
// ===== 機械特性 =====
getHardness()                  // 硬度を取得する
getStrength()                  // 強度を取得する
getToughness()                 // 靭性を取得する
// ===== 電気特性 =====
getElectricalResistance()      // 電気抵抗を取得する
getConductivity()              // 導電率を取得する
// ===== 魔術特性 =====
getMagicCapacity()             // 魔力保持量を取得する
getMagicConductivity()         // 魔力伝導率を取得する
getMagicResistance()           // 魔力抵抗を取得する
// ===== 比較 =====
compareMaterial()              // 2つの物質を比較する
calculateMaterialProperty()    // 指定条件で物質特性を計算する
// ===== 更新 =====
updateMaterialData()           // 物質データを更新する
resetMaterialData()            // データを初期化する
```

## 9. イベント
MaterialRegisteredEvent:
新しい物質が登録された時に発生する\
MaterialRemovedEvent:
物質登録が削除された時に発生する\
MaterialDataChangedEvent:
物質データが変更された時に発生する\
MaterialStateChangedEvent:
物質状態が変化した時に発生する\
CompositionChangedEvent:
物質構成が変更された時に発生する\
AlloyCreatedEvent:
新しい合金が作成された時に発生する\
PurityChangedEvent:
純度が変化した時に発生する\
MaterialPropertyChangedEvent:
物質特性が変更された時に発生する\

## 10. 使用システム
現状:
なし\

（利用するシステム完成後に記載）

## 11. 管理する単位(Unit)

Density:
kg/m³\
Mass:
kg\
Volume:
m³\
Temperature:
K\
ThermalConductivity:
W/(m・K)\
SpecificHeat:
J/(kg・K)\
Hardness:
専用値(H)\
Strength:
Pa\
ElectricalResistance:
Ω\
Conductivity:
S/m\
MagicCapacity:
Ma\
MagicConductivity:
MC\
Purity:
%\