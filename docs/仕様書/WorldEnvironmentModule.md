# WorldEnvironmentModule

## 1. 基本情報
モジュール名: WorldEnvironmentModule\
バージョン: v0.1.0 (Draft)\
担当者: (編集で記載)\
作成日: 7/11

## 2. 所属システム

所属システム:InfinityMax:GameEngine\
上位システム:ゲームエンジン\
関連モジュール:
* PhysicsModule
* MaterialModule
* DataModule
* EventModule
* SaveModule

## 3. モジュール概要

WorldEnvironmentModuleは、InfinityMax世界に存在する自然環境・惑星環境・地域環境の状態を管理する基盤モジュールである。\
世界内の気候、気温、大気、天候、時間変化、環境パラメータを管理し、他システムへ環境情報を提供する。\
本モジュールは、探索、サバイバル、建築、工業、魔術、生命システムなど幅広いシステムから利用される。

担当範囲:
* 気温管理
* 気圧管理
* 湿度管理
* 大気管理
* 天候管理
* 風管理
* 季節管理
* 時間変化
* 地域環境管理
* 高度環境管理

担当しない:
* 物理現象計算
* 物質変化計算
* 流体計算
* 魔術現象計算


## 4. 設計思想

* 世界を固定値ではなく常に変化する環境として扱う。
* 現実の気候・大気モデルを参考にする。
* 地域ごとに異なる環境状態を持てるようにする。
* 他システムは環境APIを利用して動作する。
* ワールド生成後も環境変化が可能な設計にする。
* 将来的な惑星・宇宙環境への拡張を考慮する。

## 5. 機能一覧

TemperatureEnvironmentSystem
→ 世界・地域の温度を管理する\

管理:
* 基本気温
* 日変化
* 季節変化
* 高度補正

AtmosphereSystem
→ 大気状態を管理する\

管理:
* 気圧
* 酸素濃度
* 大気成分
* 密度

WeatherSystem
→ 天候を管理する\

管理:
* 晴天
* 雨
* 雷雨
* 雪
* 霧

HumiditySystem
→ 湿度を管理する\

管理:
* 相対湿度
* 水分量
* 蒸発量

WindSystem
→ 風を管理する\

管理:
* 風速
* 風向
* 風圧

SeasonSystem
→ 季節変化を管理する\

管理:
* 春
* 夏
* 秋
* 冬
* 季節周期

TimeEnvironmentSystem
→ 時間による環境変化を管理する\

管理:
* 昼夜
* 日照量
* 太陽位置

BiomeEnvironmentSystem
→ 地域ごとの環境を管理する\

管理:
* バイオーム環境値
* 地形補正
* 生態条件

AltitudeEnvironmentSystem
→ 高度による環境変化を管理する\

管理:
* 気圧低下
* 温度低下
* 酸素量変化

EnvironmentSimulationSystem
→ 環境シミュレーション更新\

## 6. 他モジュールとの連携

利用:\
**PhysicsModule**

使用内容:
* 温度
* 圧力
* 密度
* 熱交換

**MaterialModule**\
使用内容:
* 凍結
* 融解
* 腐食条件

**DataModule**\
使用内容:
* 環境データ保存

*^EventModule**\
使用内容:
* 環境変化通知

## 7. データ

**基本環境情報**\
* Temperature（気温）
* Pressure（気圧）
* Humidity（湿度）
* WindSpeed（風速）
* WindDirection（風向）
* AirDensity（大気密度）

**大気情報**\
* OxygenRate（酸素濃度）
* NitrogenRate（窒素濃度）
* CarbonDioxideRate（二酸化炭素濃度）
* GasComposition（気体構成）

**天候情報**\
* WeatherType
* RainLevel
* SnowLevel
* CloudDensity
* LightningLevel
* FogDensity

**時間情報**\
* WorldTime
* DayTime
* Season
* SolarAngle
* SunIntensity

**地域情報**\
* BiomeID
* ClimateType
* Altitude
* Latitude
* TemperatureModifier
* WeatherModifier

**環境状態**\
* EnvironmentID
* EnvironmentState
* HazardLevel
* Habitability

## 8. API・公開関数
```Java
// ===== Temperature =====
getTemperature()                 // 現在の気温を取得する
setTemperature()                 // 気温を設定する
calculateTemperature()           // 気温を計算する
// ===== Atmosphere =====
getPressure()                    // 大気圧を取得する
getAirDensity()                  // 大気密度を取得する
getAtmosphereComposition()       // 大気構成を取得する
// ===== Humidity =====
getHumidity()                    // 湿度を取得する
setHumidity()                    // 湿度を設定する
calculateHumidity()              // 湿度を計算する
// ===== Weather =====
getWeather()                     // 現在の天候を取得する
setWeather()                     // 天候を変更する
generateWeather()                // 天候を生成する
// ===== Wind =====
getWindSpeed()                   // 風速を取得する
getWindDirection()               // 風向を取得する
calculateWind()                  // 風を計算する
// ===== Season =====
getSeason()                      // 現在の季節を取得する
changeSeason()                   // 季節を変更する
// ===== Biome =====
getEnvironmentData()             // 地域環境データを取得する
setEnvironmentData()             // 地域環境データを設定する
// ===== Altitude =====
calculateAltitudeEffect()       // 高度による環境影響を計算する
// ===== Simulation =====
updateEnvironment()              // 環境シミュレーションを更新する
resetEnvironment()               // 環境データを初期化する
```

## 9. イベント

EnvironmentTickEvent:
環境シミュレーション更新時に発生する\
TemperatureChangedEvent:
気温が変化した時に発生する\
PressureChangedEvent:
気圧が変化した時に発生する\
HumidityChangedEvent:
湿度が変化した時に発生する\
WeatherChangedEvent:
天候が変化した時に発生する\
RainStartedEvent:
雨が開始した時に発生する\
RainStoppedEvent:
雨が終了した時に発生する\
SnowStartedEvent:
雪が開始した時に発生する\
WindChangedEvent:
風速または風向が変化した時に発生する\
SeasonChangedEvent:
季節が変化した時に発生する\
DayNightChangedEvent:
昼夜状態が変化した時に発生する\
BiomeEnvironmentChangedEvent:
地域環境が変化した時に発生する\
AltitudeChangedEvent:
高度による環境状態が変化した時に発生する\
EnvironmentHazardEvent:
危険環境状態になった時に発生する\

## 10. 使用システム

現状:
なし\
（利用するシステム完成後に記載）\

## 11. 管理する単位(Unit)

Temperature:
K\
Pressure:
Pa\
Humidity:
%\
WindSpeed:
m/s\
WindDirection:
degree\
AirDensity:
kg/m³\
OxygenRate:
%\
RainLevel:
mm/h\
SnowLevel:
mm/h\
Altitude:
m\
SolarIntensity:
W/m²