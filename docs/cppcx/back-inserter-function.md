---
title: back_inserter 関数
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209443"
---
# <a name="backinserter-function"></a>back_inserter 関数

指定されたコレクションの末尾に要素を挿入するために使用される反復子を返します。

## <a name="syntax"></a>構文

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型パラメーター。

*v*<br/>
基になるコレクションへのアクセスを提供するインターフェイス ポインター。

### <a name="return-value"></a>戻り値

反復子。

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:**:Foundation

## <a name="see-also"></a>関連項目

[Windows::Foundation::Collections 名前空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
