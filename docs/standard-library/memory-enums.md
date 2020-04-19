---
title: '&lt;memory&gt; 列挙型'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257833"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 列挙型

## <a name="pointer_safety"></a>pointer_safety 列挙型

`get_pointer_safety` によって返される可能性がある値の列挙型です。

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>コメント

スコープを持つ**列挙型**は、`get_pointer_safety()`によって返される値を定義します。

`relaxed` -- 安全に派生していないポインター (明らかに、宣言されたオブジェクトまたは割り当てられたオブジェクトへのポインター) が、安全に派生したポインターと同じように扱われます。

`preferred` -- 上と同様ですが、安全に派生していないポインターを逆参照することはできません。

`strict` -- 安全に派生していないポインターは、安全に派生したポインターとは異なる方法で扱われる場合があります。
