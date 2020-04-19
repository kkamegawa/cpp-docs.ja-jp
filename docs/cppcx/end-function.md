---
title: end 関数
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::end
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
ms.openlocfilehash: c46c601be2b2ed78cf79641a7fcf5324e615a771
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375809"
---
# <a name="end-function"></a>end 関数

指定されたインターフェイス パラメーターによってアクセスされるコレクションの末尾を越えて指す反復子を返します。

## <a name="syntax"></a>構文

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
テンプレート型パラメーター。

*v*<br/>
ベクターのコレクション\<T > または VectorView\<T >、IVector によってアクセスされるオブジェクト\<T >、または IVectorView\<T > インターフェイス。

*i*<br/>
Windows ランタイムの任意のコレクション オブジェクトを IIterable によりアクセスされる\<T > インターフェイス。

### <a name="return-value"></a>戻り値

コレクションの末尾を越えて指す反復子。

### <a name="remarks"></a>Remarks

最初の 2 つのテンプレート関数は反復子を返し、3 番目のテンプレート関数は入力反復子を返します。

[によって返される](../cppcx/platform-collections-vectorviewiterator-class.md) Platform::Collections::VectorViewIterator `end` オブジェクトは、 `VectorProxy<T>`型の要素を格納するプロキシ反復子です。 ただし、プロキシ オブジェクトは、ユーザー コードにはほとんどは表示されません。 詳細については、「 [Collections (C++/CX) (コレクション (C++/CX))](../cppcx/collections-c-cx.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:**:Foundation

## <a name="see-also"></a>関連項目

[Windows::Foundation::Collections 名前空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
