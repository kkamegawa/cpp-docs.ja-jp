---
title: メモリ上書きのチェック
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342248"
---
# <a name="checking-for-memory-overwrites"></a>メモリ上書きのチェック

ヒープ操作関数の呼び出しでアクセス違反が発生した場合は、プログラムで、ヒープが破損している可能性が。 このような状況の一般的な症状は次のようになります。

```
Access Violation in _searchseg
```

[_Heapchk](../c-runtime-library/reference/heapchk.md)関数は両方のデバッグとリリース ビルド (Windows NT のみ) のランタイム ライブラリのヒープの整合性を検証します。 使用することができます`_heapchk`と同様に、`AfxCheckMemory`たとえば、ヒープの上書きを分離する関数。

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

この関数が失敗した場合、必要がありますを分離するこの時点で、ヒープが破損しています。

## <a name="see-also"></a>関連項目

[リリース ビルドの問題の解決](fixing-release-build-problems.md)
