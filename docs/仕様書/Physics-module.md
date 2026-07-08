# PhysicsModule
## 1. 基本情報

モジュール名: PhysicsModule  
バージョン: v0.1.0  
担当者:決定次第記入  
作成日:7/8  

## 2. 所属システム
所属システム: InfinityMax:GameEngine  
上位システム: ゲームエンジン  
関連モジュール:  
* (後で記載)  
* (後で記載)  
* (後で記載)  
  
## 3. モジュール概要
PhysicsModuleは、InfinityMaxにおける物理法則を管理する基盤モジュールである。
本モジュールはゲーム内で共通して利用される物理計算APIを提供し、あらゆるMOD・システムから利用されることを目的とする。

担当範囲:  
* 温度計算  
* 圧力計算  
* 密度計算  
* 質量計算  
* 体積計算  
* 流体計算  
* 気体計算  
* 状態変化計算  
* 熱伝導計算  
* 浮力・重力計算  
* 物理単位管理  

担当しない:  
* 魔法計算  
* 電力計算  
* ワールド生成  
* レンダリング  

## 4. 設計思想
* 現実の物理法則を可能な限り参考にする。
* Minecraftらしいゲーム性を損なわない範囲で簡略化する。
* 全MODが同一の物理法則を利用する。
* API中心の設計とし、他MODから自由に利用できる。
* データ駆動設計を基本とする。
* 将来的な拡張（放射線・化学・宇宙環境など）を考慮する。

## 5. 機能一覧

TemperatureSystem  
→ 温度管理・熱計算  
PressureSystem  
→ 圧力計算  
DensitySystem  
→ 密度計算  
MassSystem  
→ 質量計算  
VolumeSystem  
→ 体積計算  
FluidSystem  
→ 液体の流動計算  
GasSystem  
→ 気体の流動・膨張計算  
HeatTransferSystem  
→ 熱伝導・熱交換  
PhaseChangeSystem  
→ 固体・液体・気体の状態変化  
GravitySystem  
→ 重力計算  
BuoyancySystem  
→ 浮力計算  
PhysicsUnitSystem  
→ 物理単位管理  

## 6. 他モジュールとの連携
(全モジュール完成後に記載)  
利用  
* TODO

利用される  
* TODO

## 7. データ

保持する主要データ:
* Temperature（温度）
* Pressure（圧力）
* Density（密度）
* Mass（質量）
* Volume（体積）
* Velocity（速度）
* Acceleration（加速度）
* Force（力）
* HeatEnergy（熱エネルギー）
* InternalEnergy（内部エネルギー）
* SpecificHeat（比熱）
* ThermalConductivity（熱伝導率）
* MeltingPoint（融点）
* BoilingPoint（沸点）
* State（物質状態）
* Gravity（重力）
* Buoyancy（浮力）

## 8. API・公開関数
```Java
// ===== Temperature =====

getTemperature()                 // 保存されている温度を取得する
setTemperature()                 // 温度を設定する
addTemperature()                 // 温度を加算する
removeTemperature()              // 温度を減算する

// ===== Pressure =====

getPressure()                    // 保存されている圧力を取得する
setPressure()                    // 圧力を設定する
addPressure()                    // 圧力を加算する
removePressure()                 // 圧力を減算する
calculatePressure()              // 圧力を再計算する

// ===== Density =====

getDensity()                     // 密度を取得する
calculateDensity()               // 密度を計算する

// ===== Mass =====

getMass()                        // 質量を取得する
calculateMass()                  // 質量を計算する

// ===== Volume =====

getVolume()                      // 体積を取得する
calculateVolume()                // 体積を計算する

// ===== Velocity =====

getVelocity()                    // 速度を取得する
setVelocity()                    // 速度を設定する
calculateVelocity()              // 速度を計算する

// ===== Acceleration =====

getAcceleration()                // 加速度を取得する
calculateAcceleration()          // 加速度を計算する

// ===== Force =====

getForce()                       // 力を取得する
calculateForce()                 // 力を計算する

// ===== Heat =====

getHeatEnergy()                  // 保持している熱エネルギーを取得する
calculateHeatTransfer()          // 熱伝導を計算する
calculateHeatCapacity()          // 比熱による熱容量を計算する

// ===== Phase =====

getState()                       // 現在の物質状態を取得する
calculatePhaseChange()           // 状態変化を計算する
canPhaseChange()                 // 状態変化可能か判定する

// ===== Fluid =====

calculateFluidFlow()             // 液体の流れを計算する
canFluidFlow()                   // 液体が流れるか判定する

// ===== Gas =====

calculateGasFlow()               // 気体の流れを計算する
canGasFlow()                     // 気体が流れるか判定する

// ===== Gravity =====

calculateGravity()               // 重力を計算する
getGravity()                     // 重力値を取得する

// ===== Buoyancy =====

calculateBuoyancy()              // 浮力を計算する

// ===== Simulation =====

updatePhysics()                  // 物理シミュレーションを更新する
updateBlockPhysics()             // 指定ブロックの物理情報を更新する
updateChunkPhysics()             // チャンク単位で物理計算を更新する
resetPhysics()                   // 物理データを初期化する
```

## 9. イベント

PhysicsTickEvent: 物理シミュレーションの更新タイミングで発生する  
TemperatureChangedEvent: 温度が変更された時に発生する  
PressureChangedEvent: 圧力が変更された時に発生する  
DensityChangedEvent: 密度が変更された時に発生する  
MassChangedEvent: 質量が変更された時に発生する  
VolumeChangedEvent: 体積が変更された時に発生する  
VelocityChangedEvent: 速度が変更された時に発生する  
AccelerationChangedEvent: 加速度が変更された時に発生する  
ForceChangedEvent: 力が変更された時に発生する  
HeatEnergyChangedEvent: 熱エネルギーが変更された時に発生する  
HeatTransferEvent: 熱伝導計算が行われた時に発生する  
StateChangedEvent: 固体・液体・気体など物質状態が変化した時に発生する  
PhaseChangeEvent: 状態変化が発生した時に発生する  
FluidFlowEvent: 液体が流れた時に発生する  
GasFlowEvent: 気体が流れた時に発生する  
GravityUpdatedEvent: 重力計算が更新された時に発生する  
BuoyancyCalculatedEvent: 浮力計算が完了した時に発生する  
PhysicsResetEvent: 物理データが初期化された時に発生する  

## 10. 使用システム

(全システム完成後に記載)　　

利用されるシステム
* TODO

利用するシステム  
* TODO

## 11. 管理する単位
温度:Kelvin(K)  
圧力:Pascal(Pa)  
密度:kg/m³  
質量:kg  
体積:m³  
速度:m/s  
加速度:m/s²  
力:N  
熱量:J  
エネルギー:J  
