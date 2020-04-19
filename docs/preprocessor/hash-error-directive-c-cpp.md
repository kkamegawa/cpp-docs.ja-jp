---
title: '#error ディレクティブ (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216123"
---
# <a name="error-directive-cc"></a>#error ディレクティブ (C/C++)

**#Error**ディレクティブは、コンパイル時にユーザー指定のエラーメッセージを出力し、コンパイルを終了します。

## <a name="syntax"></a>構文

> **#error** *トークン-文字列*

## <a name="remarks"></a>Remarks

このディレクティブによって出力されるエラーメッセージには、*トークン文字列*パラメーターが含まれます。 *トークン文字列*パラメーターは、マクロの展開の対象になりません。 このディレクティブは、プリプロセス中、プログラムの不整合を開発者に通知する場合、または制約違反を発生させる場合に最も役立ちます。 次の例は、プリプロセス中のエラーの処理を示しています。

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
