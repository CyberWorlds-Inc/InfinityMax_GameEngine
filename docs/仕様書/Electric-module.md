# ElectricModule

## 1. 基本情報

モジュール名: ElectricModule\
バージョン: v0.1.0 (Draft)\
担当者: (編集で記載)\
作成日: (編集で記載)

## 2. 所属システム

所属システム:
InfinityMax:GameEngine\
上位システム:
ゲームエンジン\
関連モジュール:
* PhysicsModule
* MaterialModule
* DataModule
* NetworkModule

## 3. モジュール概要

ElectricModuleは、InfinityMax世界における電気・電力システム全般を管理する基盤モジュールである。\
現実世界の電気工学を基準とした計算モデルを採用し、発電・送電・消費・蓄電・回路制御・電気現象を提供する。\
本モジュールは工業システム、機械システム、電子機器、現代技術系MODから利用される。\

担当範囲:
* 電圧計算
* 電流計算
* 抵抗計算
* 電力計算
* 電力量計算
* 回路計算
* 交流電気
* 直流電気
* 三相交流
* 発電
* 送電
* 蓄電
* 電気部品管理
* 電気現象計算

担当しない:
* 温度変化
* 熱伝導
* 材料変化
* 物質破壊

※上記はPhysicsModuleを利用する。

## 4. 設計思想

* 現実の電気工学を基準とする。
* 電気現象を数値シミュレーションとして扱う。
* 電気設備・工業設備を統一APIで管理する。
* 直流・交流双方に対応する。
* 単純な「エネルギー値」だけではなく電気的状態を管理する。
* 高度な工業システムを構築可能にする。

## 5. 機能一覧

### 電気基本量管理
VoltageSystem\
→ 電圧管理\
CurrentSystem\
→ 電流管理\
ResistanceSystem\
→ 抵抗管理\
ConductanceSystem\
→ 導電率管理\
PowerSystem\
→ 電力管理\
EnergySystem\
→ 電力量管理

### 回路システム
CircuitSystem\
→ 電気回路管理\
SeriesCircuitSystem\
→ 直列回路計算\
ParallelCircuitSystem\
→ 並列回路計算\
CircuitAnalysisSystem\
→ 回路解析

### 交流システム
ACSystem\
→ 交流電気管理\
FrequencySystem\
→ 周波数管理\
PhaseSystem\
→ 位相管理\
ThreePhaseSystem\
→ 三相交流管理

### 発電システム
GeneratorSystem\
→ 発電機管理\
MechanicalGenerationSystem\
→ 機械エネルギーから発電\
SolarGenerationSystem\
→ 太陽光発電\
ThermalGenerationSystem\
→ 熱エネルギー発電

### 電気現象
JouleHeatSystem\
→ ジュール熱計算\
ElectromagneticSystem\
→ 電磁気現象管理\
InductionSystem\
→ 電磁誘導計算\
CapacitanceSystem\
→ 静電容量管理\
InductanceSystem\
→ インダクタンス管理

### 安全システム

OverVoltageSystem\
→ 過電圧判定\
OverCurrentSystem\
→ 過電流判定\
ShortCircuitSystem\
→ 短絡判定\
LeakCurrentSystem\
→ 漏電判定\

## 6. 他モジュールとの連携

利用:
**PhysicsModule**\

使用内容:
* ジュール熱による温度変化
* 電気抵抗の温度依存
* 発熱による物質変化

**MaterialModule**\

使用内容:
* 導電率
* 抵抗率
* 材料特性

**DataModule**\

使用内容:
* 電気設備データ保存

## 7. データ
### 基本電気量

* Voltage（電圧）
* Current（電流）
* Resistance（抵抗）
* Conductance（コンダクタンス）
* Power（電力）
* Energy（電力量）

### 回路情報

* CircuitID
* ConnectionList
* InputVoltage
* OutputVoltage
* CircuitState
* LoadResistance

### 交流情報

* Frequency（周波数）
* Phase（位相）
* RMSVoltage（実効電圧）
* RMSCurrent（実効電流）

### 三相交流

* PhaseA
* PhaseB
* PhaseC
* PhaseDifference
* ThreePhasePower

### 電気部品情報

* GeneratorData
* BatteryData
* TransformerData
* MotorData
* CapacitorData
* CoilData

### 安全情報

* MaximumVoltage
* MaximumCurrent
* TemperatureLimit
* ShortCircuitState
* LeakageState

### 8. API・公開関数
```Java
// 電圧
getVoltage()                 // 電圧を取得する
setVoltage()                 // 電圧を設定する
calculateVoltage()           // 電圧を計算する
// 電流
getCurrent()                 // 電流を取得する
setCurrent()                 // 電流を設定する
calculateCurrent()            // 電流を計算する
// 抵抗
getResistance()              // 抵抗値を取得する
setResistance()              // 抵抗値を設定する
calculateResistance()        // 抵抗を計算する
// 電力
calculatePower()             // 電力を計算する
getPower()                   // 電力を取得する
// 電力量
calculateEnergy()            // 電力量を計算する
getEnergy()                  // 電力量を取得する
// 回路
createCircuit()              // 電気回路を作成する
connectCircuit()             // 回路を接続する
disconnectCircuit()          // 回路接続を解除する
analyzeCircuit()             // 回路状態を解析する
// 交流
calculateAC()                // 交流電気を計算する
calculateFrequency()         // 周波数を計算する
calculatePhase()             // 位相を計算する
// 三相交流
calculateThreePhasePower()   // 三相交流電力を計算する
// 発電
generateElectricity()        // 電気を生成する
consumeElectricity()         // 電気を消費する
// 現象
calculateJouleHeat()         // ジュール熱を計算する
calculateInduction()         // 電磁誘導を計算する
calculateCapacitance()       // 静電容量を計算する
calculateInductance()        // インダクタンスを計算する
// 安全
checkOverVoltage()           // 過電圧を判定する
checkOverCurrent()           // 過電流を判定する
checkShortCircuit()          // 短絡を判定する
checkLeakCurrent()           // 漏電を判定する
// 更新
updateElectricSystem()       // 電気システムを更新する
resetElectricSystem()        // 電気状態を初期化する
```

## 9. イベント
ElectricTickEvent:
電気システム更新時に発生する\
VoltageChangedEvent:
電圧が変化した時に発生する\
CurrentChangedEvent:
電流が変化した時に発生する\
ResistanceChangedEvent:
抵抗値が変化した時に発生する\
PowerChangedEvent:
電力が変化した時に発生する\
EnergyChangedEvent:
電力量が変化した時に発生する\
CircuitConnectedEvent:
回路接続が成立した時に発生する\
CircuitDisconnectedEvent:
回路接続が解除された時に発生する\
ElectricGenerationEvent:
発電が行われた時に発生する\
ElectricConsumptionEvent:
電力消費が発生した時に発生する\
JouleHeatGeneratedEvent:
ジュール熱が発生した時に発生する\
InductionGeneratedEvent:
電磁誘導が発生した時に発生する\
ShortCircuitEvent:
短絡が発生した時に発生する\
OverVoltageEvent:
過電圧状態になった時に発生する\
OverCurrentEvent:
過電流状態になった時に発生する\
LeakCurrentEvent:
漏電状態になった時に発生する\

## 10. 使用システム
（全システム完成後に記載）\
利用されるシステム:
* TODO

利用するシステム:
* TODO

## 11. 管理する単位(Unit)
* Voltage:
V（ボルト）\
* Current:
A（アンペア）\
* Resistance:
Ω（オーム）\
* Power:
W（ワット）\
* Energy:
J（ジュール）\
* Frequency:
Hz（ヘルツ）\
* Capacitance:
F（ファラド）\
* Inductance:
H（ヘンリー）\
* Conductance:
S（ジーメンス）\
* Charge:
C（クーロン）\

12. 参考資料
* [オームの法則](https://techweb.rohm.co.jp/product/circuit-design/electric-circuit-design/21859/)
* [キルヒホッフの法則](https://techweb.rohm.co.jp/product/circuit-design/electric-circuit-design/21777/)
* [ジュールの法則](https://rikeilabo.com/joule-heat)
* [ファラデーの電磁誘導の法則](https://rikeilabo.com/law-of-electromagnetic-induction)
* [マクスウェル方程式](https://home.hirosaki-u.ac.jp/relativity/%E9%9B%BB%E7%A3%81%E6%B0%97%E5%AD%A6-i/%E3%83%9E%E3%82%AF%E3%82%B9%E3%82%A6%E3%82%A7%E3%83%AB%E6%96%B9%E7%A8%8B%E5%BC%8F%E3%81%AB%E7%8F%BE%E3%82%8C%E3%82%8B%E8%AB%B8%E9%87%8F%E3%81%AE%E8%A7%A3%E8%AA%AC/)
* [電気設備技術基準・電気工事関連資料](https://www.meti.go.jp/policy/safety_security/industrial_safety/law/files/dengikaishaku.pdf)
* [電気工学基礎資料](https://d-engineer.com/electric/)