---
title: _bstr_t クラス
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: f394a48c0326058be705d14fb0413e23e8052ae2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386162"
---
# <a name="bstrt-class"></a>_bstr_t クラス

**Microsoft 固有の仕様**

`_bstr_t` オブジェクトは [BSTR データ型](/previous-versions/windows/desktop/automat/bstr) をカプセル化します。クラスは、必要に応じて関数 `SysAllocString`、`SysFreeString`およびその他の `BSTR`API を呼び出すことでリソースの割り当てと割り当て解除を管理します。**_Bstr_t** クラスは過大なオーバーヘッドを回避するため参照カウントを使用します。

### <a name="construction"></a>構築

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|`_bstr_t` オブジェクトを構築します。|

### <a name="operations"></a>操作

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|`BSTR` を `BSTR` でラップされた `_bstr_t` にコピーします。|
|[Attach](../cpp/bstr-t-attach.md)|`_bstr_t` ラッパーを `BSTR` にリンクします。|
|[copy](../cpp/bstr-t-copy.md)|カプセル化された `BSTR` のコピーを生成します。|
|[Detach](../cpp/bstr-t-detach.md)|`BSTR` でラップされた `_bstr_t` を返し、`BSTR` から `_bstr_t` をデタッチします。|
|[GetAddress](../cpp/bstr-t-getaddress.md)|`BSTR` でラップされた `_bstr_t` を指します。|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|`BSTR` でラップされた `_bstr_t` の先頭を指します。|
|[length](../cpp/bstr-t-length.md)|`_bstr_t` の文字数を返します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](../cpp/bstr-t-operator-equal.md)|既存の `_bstr_t` オブジェクトに新しい値を代入します。|
|[operator +=](../cpp/bstr-t-operator-add-equal-plus.md)|`_bstr_t` の末尾に文字を追加します。|
|[operator +](../cpp/bstr-t-operator-add-equal-plus.md)|2 つの文字列を連結します。|
|[operator !](../cpp/bstr-t-operator-logical-not.md)|場合にチェック カプセル化された`BSTR`は、NULL 文字列です。|
|[operator ==、!=、<、>、<=、>=](../cpp/bstr-t-relational-operators.md)|2 つの `_bstr_t` オブジェクトを比較します。|
|[operator wchar_t\* &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|カプセル化された Unicode またはマルチバイト `BSTR` オブジェクトへのポインターを抽出します。|

**Microsoft 固有の仕様はここまで**

## <a name="requirements"></a>必要条件

**Header:** \<comutil.h>

**Lib:** comsuppw.lib または comsuppwd.lib (詳細は「[/Zc:wchar_t (wchar_t をネイティブ型として認識)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください)

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート クラス](../cpp/compiler-com-support-classes.md)
