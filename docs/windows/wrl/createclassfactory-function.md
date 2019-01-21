---
title: CreateClassFactory 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: e7e213d1b0679f17ce070de85ee9410ff9546716
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336789"
---
# <a name="createclassfactory-function"></a>CreateClassFactory 関数

指定されたクラスのインスタンスを生成するファクトリを作成します。

## <a name="syntax"></a>構文

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>パラメーター

*flags*<br/>
1 つ以上を組み合わせた[RuntimeClassType](runtimeclasstype-enumeration.md)列挙値。

*entry*<br/>
ポインターを[CreatorMap](creatormap-structure.md)パラメーターに関する情報を初期化し、登録を含む*riid*します。

*riid*<br/>
インターフェイス ID への参照

*ppFactory*<br/>
この操作は、クラス ファクトリへのポインターでは正常に完了します。 場合、

## <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="remarks"></a>Remarks

場合は、アサート エラーが出力テンプレート パラメーター*ファクトリ*インターフェイスから派生していない`IClassFactory`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Wrappers::Details 名前空間](microsoft-wrl-wrappers-details-namespace.md)