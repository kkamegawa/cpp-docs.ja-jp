---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: e27ff146c75da6e90e6336106beba714dbe7c8a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689880"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

期間と時点を表し、操作するクラスと関数を定義するために、標準ヘッダー \<chrono> を含めます。

Visual Studio 2015 以降では、安定性と単調性のC++標準要件を満たすように `steady_clock` の実装が変更されています。 現在、`steady_clock` は QueryPerformanceCounter() に基づき、`high_resolution_clock` は `steady_clock` の typedef です。 結果として、Microsoft C++コンパイラ `steady_clock::time_point` は `chrono::time_point<steady_clock>` の typedef になりました。ただし、この規則は必ずしも他の実装の場合とは限りません。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<chrono >

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|||
|-|-|
|[duration クラス](../standard-library/duration-class.md)|時間間隔を保持する型を表します。|
|[time_point クラス](../standard-library/time-point-class.md)|時点を表す型を表します。|

### <a name="structs"></a>構造体

|||
|-|-|
|[common_type 構造体](../standard-library/common-type-structure.md)|@No__t_1 と `time_point` のインスタンス化に対するクラステンプレート[common_type](../standard-library/common-type-class.md)の特殊化について説明します。|
|[duration_values 構造体](../standard-library/duration-values-structure.md)|`duration` テンプレート パラメーター `Rep` に特定の値を指定します。|
|[high_resolution_clock 構造体](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock 構造体](../standard-library/steady-clock-struct.md)|`steady` クロックを表します。|
|[system_clock 構造体](../standard-library/system-clock-structure.md)|システムのリアルタイム クロックに基づく*クロックの型*を表します。|
|[treat_as_floating_point 構造体](../standard-library/treat-as-floating-point-structure.md)|型を浮動小数点型として扱うことができるかどうかを指定します。|

### <a name="functions"></a>関数

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|`duration` オブジェクトを指定した型にキャストします。|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|`time_point` オブジェクトを指定した型にキャストします。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator-](../standard-library/chrono-operators.md#operator-)|`duration` オブジェクトおよび `time_point` オブジェクトの減算または否定の演算子。|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|`duration` オブジェクトおよび `time_point` オブジェクトで使用される非等値演算子。|
|[modulo 演算子](../standard-library/chrono-operators.md#op_modulo)|`duration` オブジェクトに対するモジュロ演算の演算子。|
|[operator*](../standard-library/chrono-operators.md#op_star)|`duration` オブジェクトの乗算演算子。|
|[operator/](../standard-library/chrono-operators.md#op_div)|`duration` オブジェクトの除算演算子。|
|[operator+](../standard-library/chrono-operators.md#op_add)|`duration` オブジェクトおよび `time_point` オブジェクトを追加します。|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値未満かどうかを判断します。|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値以下かどうかを判断します。|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|2 つの `duration` オブジェクトが同じ長さの時間間隔を表しているかどうか、または 2 つの `time_point` オブジェクトが同じ時点を表しているかどうかを判断します。|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値より大きいかどうかを判断します。|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値以上かどうかを判断します。|

### <a name="typedefs-predefined-duration-types"></a>Typedef (定義済みの期間の種類)

次の typedef で使用される比率の種類の詳細については、「[\<<ratio>](../standard-library/ratio.md)」を参照してください。

|||
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|ティック間隔が1ナノ秒の `duration` 型のシノニム。|
|`typedef duration<long long, micro> microseconds;`|ティック間隔が1マイクロ秒の `duration` 型のシノニム。|
|`typedef duration<long long, milli> milliseconds;`|ティック間隔が1ミリ秒の `duration` 型のシノニム。|
|`typedef duration<long long> seconds;`|ティック間隔が1秒の `duration` 型のシノニム。|
|`typedef duration<int, ratio<60> > minutes;`|ティック間隔が1分の `duration` 型のシノニム。|
|`typedef duration<int, ratio<3600> > hours;`|ティック間隔が1時間の `duration` 型のシノニム。|

### <a name="literals"></a>リテラル

**(C++ 11)** @No__t_1chrono > ヘッダーは、コードの利便性、タイプセーフ、および保守性を向上させるために使用できる、次の[ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)を定義します。 これらのリテラルは `literals::chrono_literals` インライン名前空間で定義されており、std::chrono がスコープに含まれている場合にスコープに含まれます。

|||
|-|-|
|hours 演算子 "" h (unsigned long long Val)|時間を整数値として指定します。|
|duration \<double、比率 \<3600 > > operator "" h (long double Val)|時間を浮動小数点値として指定します。|
|分 (演算子 "" min) (unsigned long long Val)|分を整数値として指定します。|
|duration \<double、比率 \<60 > > (operator "" min) (long double Val)|分を浮動小数点値として指定します。|
|秒演算子 "" s (unsigned long long Val)|分を整数値として指定します。|
|duration \<double > 演算子 "" s (long double Val)|秒を浮動小数点値として指定します。|
|ミリ秒演算子 "" ミリ秒 (unsigned long long Val)|ミリ秒を整数値として指定します。|
|duration \<double, > operator "" ミリ秒 (long double Val)|ミリ秒を浮動小数点値として指定します。|
|マイクロ秒演算子 "" us (unsigned long long Val)|マイクロ秒を整数値として指定します。|
|duration \<double、micro > operator "" us (long double Val)|マイクロ秒を浮動小数点値として指定します。|
|ナノ秒演算子 "" ns (unsigned long long Val)|ナノ秒を整数値として指定します。|
|duration \<double、nano > operator "" ns (long double Val)|ナノ秒を浮動小数点値として指定します。|

chrono リテラルを使用する方法の例を次に示します。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
