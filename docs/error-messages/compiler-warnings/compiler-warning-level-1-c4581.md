---
title: コンパイラの警告 (レベル 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 5931516e3f4eba91c3b7a3ab4d0ca4979ce1ed84
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965924"
---
# <a name="compiler-warning-level-1-c4581"></a>コンパイラの警告 (レベル 1) C4581

非推奨の動作: 属性を処理するために ' string2 ' ' が ' string2 ' に置き換えられました

このエラーは、visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成される可能性C++があります。パラメーターは、ビジュアル属性をチェックします。

以前のバージョンでは、属性値は引用符で囲まれているかどうかにかかわらず受け入れられていました。 値が列挙型の場合は、引用符で囲まないでください。

## <a name="example"></a>例

次の例では、C4581 が生成されます。

```cpp
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```