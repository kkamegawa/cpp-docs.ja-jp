---
title: WeakRef クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337398"
---
# <a name="weakref-class"></a>WeakRef クラス

クラシック COM ではなく、Windows ランタイムでのみ使用できる *弱い参照* を表します。 弱い参照は、アクセスできる場合とできない場合があるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[WeakRef::WeakRef コンストラクター](#weakref)|`WeakRef` クラスの新しいインスタンスを初期化します。|
|[WeakRef::~WeakRef デストラクター](#tilde-weakref)|現在のインスタンスの初期化を解除、`WeakRef`クラス。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[WeakRef::As メソッド](#as)|指定した設定`ComPtr`ポインター パラメーターを指定したインターフェイスを表します。|
|[WeakRef::AsIID メソッド](#asiid)|指定した設定`ComPtr`ポインター パラメーターを指定したインターフェイス ID を表す|
|[WeakRef::CopyTo メソッド](#copyto)|使用可能なインターフェイスへのポインターがあるなら、指定されたポインター変数にそれを割り当てます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[WeakRef::operator& 演算子](#operator-ampersand-operator)|返します、`ComPtrRef`現在を表すオブジェクトを`WeakRef`オブジェクト。|

## <a name="remarks"></a>Remarks

A`WeakRef`オブジェクトを保持する*強い参照*、これは、オブジェクトに関連付けられ、有効または無効にすることができます。 呼び出す、`As()`または`AsIID()`強い参照を取得します。 強い参照が有効な場合、関連付けられているオブジェクトにアクセスできます。 強い参照が無効な場合 (`nullptr`)、関連付けられているオブジェクトにアクセスできません。

A`WeakRef`オブジェクトは通常、外部スレッドまたはアプリケーションによって存在が制御されるオブジェクトを表すために使用します。 たとえば、構築、`WeakRef`ファイル オブジェクトへの参照からオブジェクト。 ファイルが開いている間、強い参照は有効です。 しかし、ファイルが閉じられた場合、強い参照は無効になります。

なお、Windows 10 SDK では [As](#as)、 [AsIID](#asiid) 、 [CopyTo](#copyto) の各メソッドの動作が変更されています。 以前は、これらのメソッドを呼び出した後でしたを確認する、`WeakRef`の`nullptr`が次のコードのように、強い参照を取得が正常にかどうかを決定します。

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

上記のコードは、Windows 10 SDK (以降) の使用時には機能しません。 渡されたポインターを代わりに、チェック`nullptr`します。

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>継承階層

`ComPtr`

`WeakRef`

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

**名前空間:** Microsoft::wrl

## <a name="tilde-weakref"></a>WeakRef:: ~ WeakRef デストラクター

現在のインスタンスの初期化を解除、`WeakRef`クラス。

```cpp
~WeakRef();
```

## <a name="as"></a>Weakref::as メソッド

指定した設定`ComPtr`ポインター パラメーターを指定したインターフェイスを表します。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>パラメーター

*U*<br/>
インターフェイス ID。

*ptr*<br/>
ときにこの操作が完了すると、パラメーターを表すオブジェクトを*U*します。

### <a name="return-value"></a>戻り値

- この操作が成功した場合は s_ok を返します。それ以外の場合、理由を示す HRESULT 操作に失敗し、 *ptr*に設定されている`nullptr`します。

- 現在、この操作に成功した場合は S_OK`WeakRef`オブジェクトは既に解放されています。 パラメーター *ptr*に設定されている`nullptr`します。

- 現在、この操作に成功した場合は S_OK`WeakRef`オブジェクトがパラメーターから派生していない*U*します。パラメーター *ptr*に設定されている`nullptr`します。

### <a name="remarks"></a>Remarks

場合は、エラーが出力パラメーター *U*は`IWeakReference`から派生していないまたは`IInspectable`します。

最初のテンプレートは、コードで使用する必要があるフォームです。 2 番目のテンプレートは、 [auto](../../cpp/auto-cpp.md) 型推論キーワードなどの C++ 言語の機能をサポートしている内部ヘルパーの特殊化です。

以降、Windows 10 SDK では、このメソッドが設定されていない、`WeakRef`インスタンスを`nullptr`場合は、弱い参照を取得できませんでした、避けてをチェックするコードのエラー チェック、`WeakRef`の`nullptr`します。 代わりに、チェック*ptr*の`nullptr`します。

## <a name="asiid"></a>Weakref::asiid メソッド

指定した設定`ComPtr`ポインター パラメーターを指定したインターフェイス ID を表す

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*ptr*<br/>
ときにこの操作が完了すると、パラメーターを表すオブジェクトを*riid*します。

### <a name="return-value"></a>戻り値

- この操作が成功した場合は s_ok を返します。それ以外の場合、理由を示す HRESULT 操作に失敗し、 *ptr*に設定されている`nullptr`します。

- 現在、この操作に成功した場合は S_OK`WeakRef`オブジェクトは既に解放されています。 パラメーター *ptr*に設定されている`nullptr`します。

- 現在、この操作に成功した場合は S_OK`WeakRef`オブジェクトがパラメーターから派生していない*riid*します。 パラメーター *ptr*に設定されている`nullptr`します。 (詳細については、「解説」を参照してください。)

### <a name="remarks"></a>Remarks

場合は、エラーが出力パラメーター *riid*から派生していない`IInspectable`します。 このエラーは、戻り値よりも優先されます。

最初のテンプレートは、コードで使用する必要があるフォームです。 2 番目のテンプレート (ここでは示されていないが、ヘッダー ファイルでは宣言されている) は、 [auto](../../cpp/auto-cpp.md) 型推論キーワードなどの C++ 言語の機能をサポートしている内部ヘルパーの特殊化です。

以降、Windows 10 SDK では、このメソッドが設定されていない、`WeakRef`インスタンスを`nullptr`場合は、弱い参照を取得できませんでした、避けてをチェックするコードのエラー チェック、`WeakRef`の`nullptr`します。 代わりに、チェック*ptr*の`nullptr`します。

## <a name="copyto"></a>Weakref::copyto メソッド

使用可能なインターフェイスへのポインターがあるなら、指定されたポインター変数にそれを割り当てます。

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>パラメーター

*U*<br/>
ポインター、`IInspectable`インターフェイス。 場合は、エラーが出力*U*から派生していない`IInspectable`します。

*riid*<br/>
インターフェイス ID。 場合は、エラーが出力*riid*から派生していない`IWeakReference`します。

*ptr*<br/>
二重間接ポインター`IInspectable`または`IWeakReference`します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。 詳細については、「**解説**」をご覧ください。

### <a name="remarks"></a>Remarks

S_OK の戻り値はこの操作が成功したことを示しますが、弱い参照が強い参照に解決されたかどうかは示していません。 S_OK が返された場合は、そのパラメーターをテスト*p*が強力な参照、つまりパラメーター *p*と等しくない`nullptr`します。

以降、Windows 10 SDK では、このメソッドが設定されていない、`WeakRef`インスタンス`nullptr`場合は、弱い参照を取得できませんでした、避けてエラーをチェックするコードをチェック、`WeakRef`の`nullptr`します。 代わりに、チェック*ptr*の`nullptr`します。

## <a name="operator-ampersand-operator"></a>Weakref::operator&amp;演算子

返します、`ComPtrRef`現在を表すオブジェクトを`WeakRef`オブジェクト。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>戻り値

A`ComPtrRef`現在を表すオブジェクトを`WeakRef`オブジェクト。

### <a name="remarks"></a>Remarks

これは、内部ヘルパー演算子が、コードで使用されるものではありません。

## <a name="weakref"></a>Weakref::weakref コンス トラクター

`WeakRef` クラスの新しいインスタンスを初期化します。

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>パラメーター

*ptr*<br/>
ポインター、参照、または現在を初期化する既存のオブジェクトへの右辺値参照`WeakRef`オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンス トラクターによって初期化空`WeakRef`オブジェクト。 2 番目のコンス トラクターによって初期化、`WeakRef`オブジェクトへのポインターから、`IWeakReference`インターフェイス。 3 番目のコンス トラクターによって初期化、`WeakRef`への参照からオブジェクトを`ComPtr<IWeakReference>`オブジェクト。 4 番目と 5 番目のコンス トラクターの初期化、`WeakRef`から別のオブジェクト`WeakRef`オブジェクト。
