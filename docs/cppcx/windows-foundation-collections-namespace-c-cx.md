---
title: Windows::Foundation::Collections 名前空間 (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections
helpviewer_keywords:
- Windows::Foundation::Collections Namespace (C++/CX)
ms.assetid: 04bd3543-e30f-4fd2-95ee-272a3fcd0158
ms.openlocfilehash: 9a8118886f4556343f2e4a494fdbea6d240d1c77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404612"
---
# <a name="windowsfoundationcollections-namespace-ccx"></a>Windows::Foundation::Collections 名前空間 (C++/CX)

C++/CX では、Vector、VectorView、マップ、および MapView コレクション クラスを使用して単純化する関数を持つ:foundation 名前空間を補足します。

## <a name="syntax"></a>構文

```

namespace Windows {
    namespace Foundation {
        namespace Collections;
    }
}
```

### <a name="functions"></a>関数

|名前|説明|
|----------|-----------------|
|[back_inserter 関数](../cppcx/back-inserter-function.md)|コレクションの末尾に値を挿入するために使用できる反復子を返します。|
|[begin 関数](../cppcx/begin-function.md)|コレクションの先頭を指す反復子を返します。|
|[end 関数](../cppcx/end-function.md)|コレクションの末尾を越えて指す反復子を返します。|
|[to_vector 関数](../cppcx/to-vector-function.md)|コレクションを std::vector として返します。|

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:**:Foundation
