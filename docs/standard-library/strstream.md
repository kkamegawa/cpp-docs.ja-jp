---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: ecf8499a07f03c00588e7b7fd83b8d41a23e8e7a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459083"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

**Char**オブジェクトの割り当てられた配列に格納されているシーケンスに対する iostreams 操作をサポートする複数のクラスを定義します。 このようなシーケンスは、C 文字列と簡単に相互変換できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<strstream>

**名前空間:** std

## <a name="remarks"></a>Remarks

型 `strstream` のオブジェクトは C 文字列の `char` * を使用します。 [\<sstream](../standard-library/sstream.md) は、型 [basic_string](../standard-library/basic-string-class.md) のオブジェクトを操作するために使用します。

> [!NOTE]
> Strstream > \<のクラスは非推奨とされます。 代わりに sstream > で\<クラスを使用することを検討してください。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|||
|-|-|
|[strstreambuf クラス](../standard-library/strstreambuf-class.md)|クラスは、 **char**配列オブジェクトに格納されている要素のシーケンスとの間での要素の転送を制御するストリームバッファーを記述します。|
|[istrstream クラス](../standard-library/istrstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーからの、要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを表します。|
|[ostrstream クラス](../standard-library/ostrstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーへの、要素とエンコードされたオブジェクトの挿入を制御するオブジェクトを表します。|
|[strstream クラス](../standard-library/strstream-class.md)|このクラスは、クラス [strstreambuf](../standard-library/strstreambuf-class.md) のストリーム バッファーを使用して要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを表します。|

### <a name="functions"></a>関数

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>関連項目

[\<strstream>](../standard-library/strstream.md)\
[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
