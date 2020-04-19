---
title: インポート属性の名前の変更
ms.date: 08/29/2019
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: ef1f64e0c268f850899efe499f7b1ad3991dd570
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216665"
---
# <a name="rename-import-attribute"></a>インポート属性の名前の変更

**C++のみ**

名前の衝突の問題を回避します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***rename (** "*OldName*" **,** "*NewName*" **)**

### <a name="parameters"></a>パラメーター

*OldName*\
タイプ ライブラリ内の古い名前。

*NewName*\
古い名前の代わりに使用する名前。

## <a name="remarks"></a>Remarks

**Rename**属性が指定されている場合、コンパイラは、 *OldName*のすべての出現箇所を、結果のヘッダーファイル内でユーザーが指定した*NewName*に置き換えます。

**Rename**属性は、タイプライブラリ内の名前がシステムヘッダーファイル内のマクロ定義と一致する場合に使用できます。 この状況が解決されない場合、コンパイラは[コンパイラエラー C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md)や[コンパイラエラー C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)など、さまざまな構文エラーを発行する可能性があります。

> [!NOTE]
> 置換は、結果のヘッダー ファイルで使用される名前ではなく、タイプ ライブラリで使用される名前に対して実行されます。

たとえば `MyParent` という名前のプロパティがタイプ ライブラリにあり、マクロ `GetMyParent` がヘッダー ファイルに定義され、`#import` の前で使用されているとします。 は`GetMyParent` 、エラー処理`get`プロパティのラッパー関数の既定の名前であるため、名前の競合が発生します。 問題を回避するには、`#import` ステートメント内で次の属性を使用します。

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

これにより、タイプ ライブラリ内の `MyParent` の名前が変更されます。 `GetMyParent` ラッパーの名前を変更しようとすると、失敗します:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

これは、名前`GetMyParent`が結果のタイプライブラリのヘッダーファイルでのみ発生するためです。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
