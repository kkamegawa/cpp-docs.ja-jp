---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 3838e215ffac42ec6902ab6a9837f638153cf184
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689166"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Iostreams の挿入を仲介するクラステンプレート[basic_ostream](../standard-library/basic-ostream-class.md)を定義します。 ヘッダーは、関連する複数のマニピュレーターを定義します (通常このヘッダーは、別の iostream ヘッダーに含まれています。 まれに、直接含めなければならないことがあります)。

## <a name="syntax"></a>構文

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|**Char で**特殊化された `basic_ostream` から型を作成し、 **char**に特化した `char_traits` します。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|**Wchar_t で**特殊化された `basic_ostream` から型を作成し、 **wchar_t**に特化した `char_traits` します。|

### <a name="manipulators"></a>マニピュレーター

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|行を終了し、バッファーをフラッシュします。|
|[ends](../standard-library/ostream-functions.md#ends)|文字列を終了します。|
|[flush](../standard-library/ostream-functions.md#flush)|バッファーをフラッシュします。|
|[swap](../standard-library/ostream-functions.md#swap)|左側の `basic_ostream` オブジェクト パラメーターの値と右側の `basic_ostream` オブジェクト パラメーターの値を交換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|さまざまな型をストリームに書き込みます。|

### <a name="classes"></a>クラス

|インスタンス|説明|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|クラステンプレートは、要素とエンコードされたオブジェクトのストリームバッファーへの挿入を制御するオブジェクトを表します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
