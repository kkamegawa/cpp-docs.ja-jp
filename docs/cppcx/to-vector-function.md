---
title: to_vector 関数
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: 4fa4e9c620519cc6bb2f96d346ded88b6cc826ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404625"
---
# <a name="tovector-function"></a>to_vector 関数

値が、指定された IVector または IVectorView パラメーターの基になるコレクションと同じである `std::vector` を返します。

## <a name="syntax"></a>構文

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型パラメーター。

*v*<br/>
基になる Vector または VectorView オブジェクトへのアクセスを提供する IVector または IVectorView インターフェイス。

### <a name="return-value"></a>戻り値

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:**:Foundation

## <a name="see-also"></a>関連項目

[Windows::Foundation::Collections 名前空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
