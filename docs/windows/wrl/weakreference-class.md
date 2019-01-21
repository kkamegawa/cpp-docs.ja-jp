---
title: WeakReference クラス
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a3372a176a158dd9c89eb888c8deb0244eef9a84
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336661"
---
# <a name="weakreference-class"></a>WeakReference クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
class WeakReference;
```

## <a name="remarks"></a>Remarks

表す、*弱い参照*Windows ランタイムまたはクラシック COM で使用できます。 弱い参照は、アクセスできる場合とできない場合があるオブジェクトを表します。

A`WeakReference`オブジェクトを保持、*強い参照*、オブジェクトへのポインターであると*強力な参照カウント*、これは、強い参照によって配布されたのコピーの数`Resolve()`メソッド。 強力な参照カウントが 0 以外の場合、強い参照が有効なと、オブジェクトにアクセスします。 強力な参照カウントがゼロになったら、強い参照が有効でないし、オブジェクトにアクセスできません。

A`WeakReference`オブジェクトは通常、外部スレッドまたはアプリケーションによって存在が制御されるオブジェクトを表すために使用します。 たとえば、構築、`WeakReference`ファイル オブジェクトへの参照からオブジェクト。 ファイルが開いている間、強い参照は有効です。 しかし、ファイルが閉じられた場合、強い参照は無効になります。

`WeakReference`メソッドはスレッド セーフであります。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                  | 説明
----------------------------------------------------- | ---------------------------------------------------------------------------
[Weakreference::weakreference](#weakreference)        | `WeakReference` クラスの新しいインスタンスを初期化します。
[WeakReference:: ~ WeakReference](#tilde-weakreference) | 初期化を解除 (破棄) の現在のインスタンス、`WeakReference`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                                                 | 説明
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | 強い参照が現在のカウントをデクリメント`WeakReference`オブジェクト。
[WeakReference::IncrementStrongReference](#incrementstrongreference) | 現在の強い参照カウントをインクリメント`WeakReference`オブジェクト。
[WeakReference::Resolve](#resolve)                                   | 強力な参照カウントが 0 以外の場合、現在の強い参照値に指定されたポインターを設定します。
[Weakreference::setunknown](#setunknown)                             | 現在の強い参照を設定`WeakReference`オブジェクトを指定されたインターフェイス ポインター。

## <a name="inheritance-hierarchy"></a>継承階層

`WeakReference`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

現在のインスタンスの初期化を解除、`WeakReference`クラス。

## <a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Remarks

強い参照が現在のカウントをデクリメント`WeakReference`オブジェクト。

強い参照に設定されている強力な参照カウントがゼロになったら、`nullptr`します。

### <a name="return-value"></a>戻り値

デクリメントされた強い参照数。

## <a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>戻り値

インクリメントされた強い参照数。

### <a name="remarks"></a>Remarks

現在の強い参照カウントをインクリメント`WeakReference`オブジェクト。

## <a name="resolve"></a>Weakreference::resolve

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*ppvObject*<br/>
この操作が完了するとは、強力な参照カウントが 0 以外の場合は、現在の強い参照のコピーします。

### <a name="return-value"></a>戻り値

- この操作が成功し、強い参照カウントがゼロの場合は s_ok を返します。 *PpvObject*にパラメーターが設定されている`nullptr`します。

- この操作が成功し、強力な参照カウントが 0 以外の場合は s_ok を返します。 *PpvObject*パラメーターが強い参照に設定します。

- それ以外の場合、理由を示す HRESULT をこの操作に失敗しました。

### <a name="remarks"></a>Remarks

強力な参照カウントが 0 以外の場合、現在の強い参照値に指定されたポインターを設定します。

## <a name="setunknown"></a>Weakreference::setunknown

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>パラメーター

*unk*<br/>
ポインター、`IUnknown`オブジェクトのインターフェイス。

### <a name="remarks"></a>Remarks

現在の強い参照を設定`WeakReference`オブジェクトを指定されたインターフェイス ポインター。

## <a name="weakreference"></a>Weakreference::weakreference

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
WeakReference();
```

### <a name="remarks"></a>Remarks

`WeakReference` クラスの新しいインスタンスを初期化します。

強い参照ポインター、`WeakReference`オブジェクトが初期化`nullptr`、し、強力な参照カウントは 1 に初期化されます。
