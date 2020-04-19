---
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: a322e517a4adb51879fc2a60f6c08f6561276de9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689508"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

iostream 操作の基礎となる型と関数を定義します。 このヘッダーは通常、別の iostream ヘッダーによってインクルードされており、ユーザーが直接インクルードすることはほとんどありません。

## <a name="requirements"></a>［要件］

**ヘッダー**: \<ios >

**名前空間:** std

> [!NOTE]
> @No__t_0ios > ライブラリは `#include <iosfwd>` ステートメントを使用します。

## <a name="remarks"></a>Remarks

マニピュレーターとは、多種類の関数のグループです。 \<ios> 内で宣言されたマニピュレーターは、[ios_base](../standard-library/ios-base-class.md) クラスの引数オブジェクトに格納された値を変更します。 他のマニピュレーターは、このクラスから派生した型のオブジェクトによって制御されるストリームに対して操作を実行します。たとえば、クラステンプレート[basic_istream](../standard-library/basic-istream-class.md)または[basic_ostream](../standard-library/basic-ostream-class.md)の1つを特殊化しています。 たとえば、 [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) は、オブジェクト `str` 内の `ios_base::skipws` の書式設定フラグをクリアします。これは、次のいずれかの型になります。

マニピュレーターは、出力ストリームに挿入したり、入力ストリームから抽出したりすることでも呼び出すことができます。これは、`ios_base` から派生したクラスに特殊な挿入演算子と抽出演算子が指定されるためです。 (例:

```cpp
istr>> noskipws;
```

[noskipws](../standard-library/ios-functions.md#noskipws)(**istr**) を呼び出します。

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[ios](../standard-library/ios-typedefs.md#ios)|従来の iostream ライブラリの ios クラスをサポートします。|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|内部操作をサポートします。|
|[streampos](../standard-library/ios-typedefs.md#streampos)|バッファー ポインターまたはファイル ポインターの現在の位置を保持します。|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|ストリームのサイズを指定します。|
|[wios](../standard-library/ios-typedefs.md#wios)|従来の iostream ライブラリの wios クラスをサポートします。|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|バッファー ポインターまたはファイル ポインターの現在の位置を保持します。|

### <a name="manipulators"></a>マニピュレーター

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|[bool](../cpp/bool-cpp.md) 型の変数をストリームで **true** または **false** として表示するように指定します。|
|[dec](../standard-library/ios-functions.md#dec)|整数変数を 10 進表記で表示するように指定します。|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|浮動小数値に既定の表示形式を使用するように、`ios_base` オブジェクトのフラグを構成します。|
|[fixed](../standard-library/ios-functions.md#fixed)|浮動小数点数を固定 10 進表記で表示するように指定します。|
|[hex](../standard-library/ios-functions.md#hex)|整数変数を 16 進表記で表示するように指定します。|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|数値の符号を左揃え、数値を右揃えにします。|
|[left](../standard-library/ios-functions.md#left)|出力幅に満たないテキストをストリーム フラッシュで左揃えに表示します。|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|[bool](../cpp/bool-cpp.md) 型の変数をストリームで 1 または 0 として表示するように指定します。|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|指定している数値表記の基底の設定をオフにします。|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|小数部分が 0 の浮動小数点数の整数部分のみを表示します。|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|正の数値に明示的に符号を付けないようにします。|
|[noskipws](../standard-library/ios-functions.md#noskipws)|入力ストリームで空白を読み取るようにします。|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|出力をバッファーし、バッファーが一杯になると、出力を処理します。|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|16 進数と指数表記の指数を小文字で表示します。|
|[oct](../standard-library/ios-functions.md#oct)|整数変数を 8 進表記で表示するように指定します。|
|[right](../standard-library/ios-functions.md#right)|出力幅に満たないテキストをストリーム フラッシュで右揃えに表示します。|
|[scientific](../standard-library/ios-functions.md#scientific)|浮動小数点数値を指数表記を使用して表示します。|
|[showbase](../standard-library/ios-functions.md#showbase)|数値表記の基底を指定します。|
|[showpoint](../standard-library/ios-functions.md#showpoint)|小数部分が 0 のときも浮動小数点数の整数部分と小数点の右側にある数字を表示します。|
|[showpos](../standard-library/ios-functions.md#showpos)|正の数値に明示的に符号を付けます。|
|[skipws](../standard-library/ios-functions.md#skipws)|入力ストリームで空白を読み飛ばします。|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|バッファーが空ではないときに、出力を処理します。|
|[uppercase](../standard-library/ios-functions.md#uppercase)|16 進数と指数表記の指数を大文字で表示します。|

### <a name="error-reporting"></a>エラー報告

|||
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>クラス

|||
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|クラステンプレートは、テンプレートパラメーターに依存する、(クラステンプレート[basic_istream](../standard-library/basic-istream-class.md)の) 入力ストリームと出力ストリーム (クラステンプレート[basic_ostream](../standard-library/basic-ostream-class.md)) の両方に共通するストレージおよびメンバー関数を記述します。|
|[fpos](../standard-library/fpos-class.md)|クラステンプレートは、任意のストリーム内の任意のファイル位置インジケーターを復元するために必要なすべての情報を格納できるオブジェクトを表します。|
|[ios_base](../standard-library/ios-base-class.md)|このクラスは、テンプレート パラメーターに依存しない、入力ストリームと出力ストリームの両方に共通のストレージとメンバー関数を表します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
