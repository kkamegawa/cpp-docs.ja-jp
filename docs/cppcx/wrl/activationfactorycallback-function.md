---
title: ActivationFactoryCallback 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 4743e7724c5aba4171cb017654267afaac676f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303878"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 関数

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>パラメーター

*activationId*<br/>
ランタイム クラス名を指定する文字列へのハンドルします。

*ppFactory*<br/>
ときにこの操作が完了すると、パラメーターに対応するアクティベーション ファクトリ*activationId*します。

## <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。 可能性の高いエラー Hresult CLASS_E_CLASSNOTAVAILABLE、E_INVALIDARG です。

## <a name="remarks"></a>Remarks

指定されたアクティブ化 ID のアクティベーション ファクトリを取得します。

Windows ランタイムでは、ランタイム クラス名で指定されたオブジェクトを要求するには、このコールバック関数を呼び出します。

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)