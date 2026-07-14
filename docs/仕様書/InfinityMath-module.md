# InfinityMathModule

## 1. 基本情報

モジュール名: InfinityMathModule\
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
* ElectricModule
* MagicModule
* MaterialModule
* WorldEnvironmentModule

## 3. モジュール概要

InfinityMathModuleは、InfinityMax内で使用される共通数学処理・数値解析機能を提供する基盤モジュールである。\
各モジュールが個別に計算処理を実装することを防ぎ、統一された数学APIを提供する。\
担当範囲:

* 物理計算補助
* 電気計算補助
* 魔術計算補助
* 単位変換
* ベクトル計算
* 数値補間
* 数値制限
* 方程式処理

担当しない:

* 個別システムの計算式
* 電気公式
* 物理法則
* 魔術法則

## 4. 設計思想

* Java標準Mathで不足するゲームシミュレーション向け機能を提供する。
* 全モジュールで同じ計算方法を使用する。
* 浮動小数点誤差を管理する。
* 将来的な高度シミュレーションに対応する。
* 計算式の重複実装を防止する。

## 5. 機能一覧

BasicCalculationSystem 
→ 基本数学計算\
機能:

* 四則演算補助
* 最大値・最小値
* 範囲制限
* 絶対値処理

VectorSystem
→ ベクトル計算\
利用:

PhysicsModule\
WorldEnvironmentModule

機能:

* 位置計算
* 速度計算
* 力計算
* 方向計算

MatrixSystem → 行列計算\
利用:

* 座標変換
* 物理計算

InterpolationSystem
→ 補間計算\
利用:

* 温度変化
* 電力変化
* 魔力変化

機能:

* 線形補間
* 曲線補間

UnitConversionSystem
→ 単位変換\
利用:
全モジュール\
機能:

* 温度変換
* 圧力変換
* エネルギー変換
* 電力単位変換

NumericalAnalysisSystem
→ 数値解析\
利用:

PhysicsModule
MagicModule
ElectricModule

機能:

* 方程式近似
* 収束計算
* 微分近似

ProbabilitySystem
→ 確率計算\
利用:

MagicModule
WorldEnvironmentModule

機能:

* 発生確率
* ランダム分布

FormulaSystem
→ 共通公式計算\
利用:

PhysicsModule
ElectricModule
MagicModule

## 6. 他モジュールとの連携

利用される

**PhysicsModule**

使用:

* 物理方程式計算
* ベクトル計算
* 数値解析

**ElectricModule**

使用:

* 電気公式計算
* 交流計算
* 回路計算

**MagicModule**

使用:

* 魔術出力計算
* 反応計算

**WorldEnvironmentModule**

使用:

* 環境補間
* 気候計算

**MaterialModule**

使用:

* 材料比較計算

## 7. データ

保持する主要データ

### 数学定数

* PI
* E
* GravityConstant

### 計算精度

* CalculationPrecision
* FloatingErrorTolerance

### ベクトル情報

* Vector2
* Vector3
* Vector4

### 行列情報

* Matrix2
* Matrix3
* Matrix4

### 単位情報

* UnitType
* ConversionRate

## 8. API・公開関数
```
// 基本
clamp()
 // 数値を指定範囲内に制限する
lerp()
 // 2つの値を線形補間する
inverseLerp()
 // 補間率を逆算する
// ベクトル
calculateDistance()
 // 2点間距離を計算する
calculateDirection()
 // 方向ベクトルを計算する
normalizeVector()
 // ベクトルを正規化する
dotProduct()
 // 内積を計算する
crossProduct()
 // 外積を計算する
// 数値解析
solveEquation()
 // 方程式を近似的に解く
differentiate()
 // 微分値を計算する
integrate()
 // 積分値を計算する
// 単位変換
convertUnit()
 // 単位を変換する
// 確率
calculateProbability()
 // 発生確率を計算する
randomRange()
 // 指定範囲の乱数を生成する
// 更新
updateCalculation()
 // 計算処理を更新する
```

## 9. イベント

CalculationErrorEvent:
計算エラーが発生した時\
PrecisionWarningEvent:
計算精度不足を検出した時\
CalculationCompletedEvent:
計算処理が完了した時\
UnitConversionEvent:
単位変換が実行された時\

## 10. 使用システム

現状:
なし

（利用するシステム完成後に記載）
11. 管理する単位(Unit)

Distance:
m\
Time:
s
Velocity:
m/s\
Acceleration:
m/s²\
Force:
N\
Energy:
J\
Power:
W\
Temperature:
K\
Pressure:
Pa\
Voltage:
V\
Current:
A\
Resistance:
Ω