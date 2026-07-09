# MagicModule

## 1. 基本情報
モジュール名: MagicModule\
バージョン: v0.1.0 (Draft)\
担当者: (編集で記載)\
作成日: (編集で記載)

## 2. 所属システム
所属システム:
InfinityMax:GameEngine\
上位システム:
ゲームエンジン\
関連モジュール:
* (後で記載)
* (後で記載)
* (後で記載)

## 3. モジュール概要
MagicModuleは、InfinityMax世界に存在する **魔術元素マジカニウム**(元素番号110番、元素記号Ma)を管理する基盤モジュールである。\
本モジュールでは魔法そのものは扱わず、魔術を成立させるために必要な基礎データ・物理量・情報値・化学反応の判定を管理する。

担当範囲:
* マジカニウム管理
* 魔力密度管理
* 情報値管理
* 属性管理
* 魔術反応判定
* 魔力計算
* 魔力消費
* 魔力回復
* 魔術出力計算
* 魔力単位管理

担当しない:
* 魔法の実装
* 魔法詠唱
* 魔法エフェクト
* 魔法ダメージ
* 魔法AI

## 4. 設計思想
* 魔術は「超常現象」ではなく、マジカニウムによる自然現象として扱う。
* マジカニウムは物質として存在し、現実の元素と同様に物理的性質を持つ。
* 魔術は情報値とマジカニウムの反応によって発生する。
* 全MODが共通の魔力計算を利用する。
* 魔法ではなく「魔術基盤API」を提供する。

## 5.機能一覧
MagicaniumSystem
→ マジカニウム管理\
MagicDensitySystem
→ 魔力密度管理\
MagicStorageSystem
→ 物体内の保有量管理\
MagicTransferSystem
→ マジカニウム移動\
MagicReactionSystem
→ 魔術反応判定\
InformationValueSystem
→ 情報値管理\
MagicAttributeSystem
→ 属性管理\
MagicOutputSystem
→ 魔術出力計算\
MagicRecoverySystem
→ 魔力回復\
MagicConsumptionSystem
→ 魔力消費\
MagicUnitSystem
→ 魔力単位管理

## 6. 他モジュールとの連携
（全モジュール完成後に記載）\
利用:
* TODO

利用される:
* TODO

## 7. データ

保持する主要データ:
* MagicDensity（空間魔力密度）
* MagicAmount（保有マジカニウム量）
* MaximumMagicAmount（最大保持量）
* MagicPurity（純度）
* MagicOutputCoefficient（魔術出力係数）
* MagicConductivity（魔力伝導率）
* MagicResistance（魔力抵抗）
* MagicPermeability（魔力透過率）
* MagicTemperatureCoefficient（温度係数）
* MagicPressureCoefficient（圧力係数）
* InformationValue（情報値）
* AttributeType（属性）
* IonizationState（イオン化状態）
* MagicReactionState（反応状態）
* MagicState（気体・液体・固体・合金）
* MagicDecayRate（自然減衰率）
* MagicGenerationRate（生成率）
* MagicConsumptionRate（消費率）
* MagicRecoveryRate（回復率）
なお、InformationValueにおいては以下のパラメータを最低限持つものとする
```Java
class InformationValue {
    String attribute;   // 感情・怨念・記憶・意思などの種類
    double value;       // 情報量
}
```
## 8. API・公開関数
```Java
// ===== Density =====
getMagicDensity()                     // 空間中のマジカニウム密度を取得する
setMagicDensity()                     // 空間中のマジカニウム密度を設定する
addMagicDensity()                     // 密度を加算する
removeMagicDensity()                  // 密度を減算する
calculateMagicDensity()               // 密度を再計算する
// ===== Storage =====
getMagicAmount()                      // 保有マジカニウム量を取得する
setMagicAmount()                      // 保有量を設定する
addMagicAmount()                      // 保有量を加算する
removeMagicAmount()                   // 保有量を減算する
getMaximumMagicAmount()               // 最大保持量を取得する
// ===== Information =====
getInformationValues()                // 情報値一覧を取得する
addInformationValue()                 // 情報値を追加する
removeInformationValue()              // 情報値を削除する
clearInformationValues()              // 情報値を全削除する
hasInformationValue()                 // 指定した情報値を保持しているか判定する
// ===== Attribute =====
getAttributes()                       // 属性一覧を取得する
addAttribute()                        // 属性を追加する
removeAttribute()                     // 属性を削除する
hasAttribute()                        // 属性を保持しているか判定する
// ===== Reaction =====
calculateMagicReaction()              // 魔術反応を計算する
canMagicReaction()                    // 魔術反応可能か判定する
// ===== Output =====
calculateMagicOutput()                // 魔術出力を計算する
getMagicOutputCoefficient()           // 出力係数を取得する
setMagicOutputCoefficient()           // 出力係数を設定する
// ===== Consumption =====
consumeMagic()                        // マジカニウムを消費する
recoverMagic()                        // マジカニウムを回復する
// ===== Transfer =====
transferMagic()                       // マジカニウムを移動する
canTransferMagic()                    // 移動可能か判定する
// ===== State =====
getMagicState()                       // マジカニウムの状態を取得する
setMagicState()                       // マジカニウムの状態を設定する
isIonized()                           // イオン化しているか判定する
// ===== Update =====
updateMagic()                         // 魔力シミュレーションを更新する
resetMagic()                          // 魔力データを初期化する
```

## 9. イベント
MagicTickEvent: 魔力シミュレーション更新時に発生する\
MagicDensityChangedEvent: 空間魔力密度が変更された時に発生する\
MagicAmountChangedEvent: 保有マジカニウム量が変更された時に発生する\
MaximumMagicAmountChangedEvent: 最大保持量が変更された時に発生する\
InformationValueAddedEvent: 情報値が追加された時に発生する\
InformationValueRemovedEvent: 情報値が削除された時に発生する\
AttributeAddedEvent: 属性が追加された時に発生する\
AttributeRemovedEvent: 属性が削除された時に発生する\
MagicReactionEvent: 魔術反応が発生した時に発生する\
MagicOutputCalculatedEvent: 魔術出力の計算が完了した時に発生する\
MagicConsumedEvent: マジカニウムが消費された時に発生する\
MagicRecoveredEvent: マジカニウムが回復した時に発生する\
MagicTransferredEvent: マジカニウムが移動した時に発生する\
MagicStateChangedEvent: マジカニウムの状態が変化した時に発生する\
MagicIonizedEvent: マジカニウムがイオン化した時に発生する\
MagicNeutralizedEvent: イオン化が解除された時に発生する\
MagicResetEvent: 魔力データが初期化された時に発生する

## 10. 使用システム
（全システム完成後に記載）\
利用されるシステム:
* TODO

利用するシステム:
* TODO

## 11. 管理する単位(Unit)
* MagicDensity：Ma/m³（空間中のマジカニウム密度）
* MagicAmount：Ma（保有マジカニウム量）
* MagicOutput：MO（魔術出力）
* MagicConductivity：MC（魔力伝導率）
* MagicResistance：MR（魔力抵抗）
* MagicPermeability：MPe（魔力透過率）
* InformationValue：IV（情報値）
* MagicPurity：%（純度）
* MagicDecayRate：Ma/s（自然減衰率）
* MagicRecoveryRate：Ma/s（回復率）
