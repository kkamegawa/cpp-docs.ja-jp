---
title: begin 関数
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258292"
---
# <a name="begin-function"></a>begin 関数

指定されたインターフェイス パラメーターによってアクセスされるコレクションの先頭を指す反復子を返します。

## <a name="syntax"></a>構文

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型パラメーター。

*v*<br/>
ベクターのコレクション\<T > または VectorView\<T >、IVector によってアクセスされるオブジェクト\<T > または IVectorView\<T > インターフェイス。

*i*<br/>
IIterable によってアクセスされる任意の Windows ランタイム オブジェクトのコレクション\<T > インターフェイス。

### <a name="return-value"></a>戻り値

コレクションの先頭を指す反復子。

### <a name="remarks"></a>Remarks

最初の 2 つのテンプレート関数は反復子を返し、3 番目のテンプレート関数は入力反復子を返します。

によって返されるオブジェクトの開始の VectorIterator の型 VectorProxy 要素を格納するプロキシ反復子は、\<T >。 ただし、プロキシ オブジェクトは、ユーザー コードにはほとんどは表示されません。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:**:Foundation

## <a name="see-also"></a>関連項目

[Windows::Foundation::Collections 名前空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
