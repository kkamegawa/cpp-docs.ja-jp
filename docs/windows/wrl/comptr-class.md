---
title: ComPtr クラス
ms.date: 10/01/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: da6d0761b60257bc4b0232123d179e9c04465844
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336637"
---
# <a name="comptr-class"></a>ComPtr クラス

テンプレート パラメーターで指定されたインターフェイスを表す *スマート ポインター* 型を作成します。 `ComPtr` は、基になるインターフェイス ポインターの参照カウントを維持し、参照カウントがゼロになるとそのインターフェイスを自動的に解放します。

## <a name="syntax"></a>構文

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
インターフェイスを`ComPtr`を表します。

*U*<br/>
クラスを現在`ComPtr`フレンドです。 (このパラメーターを使用するテンプレートは保護されています)。

## <a name="remarks"></a>Remarks

`ComPtr<>` 基になるインターフェイス ポインターを表す型を宣言します。 使用して、`ComPtr<>`変数を宣言し、矢印のメンバー アクセス演算子を使用 (`->`) インターフェイスのメンバー関数にアクセスします。

スマート ポインターの詳細については、の「COM スマート ポインター」サブセクションを参照してください、 [COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices) MSDN ライブラリの「します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前            | 説明
--------------- | ---------------------------------------------------------------
`InterfaceType` | 指定された型のシノニム、 *T*テンプレート パラメーター。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                             | 説明
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[Comptr::comptr](#comptr)        | `ComPtr` クラスの新しいインスタンスを初期化します。 オーバーロードは、既定、コピー、移動、および変換の各コンストラクターを提供します。
[ComPtr:: ~ ComPtr](#tilde-comptr) | インスタンスを初期化解除`ComPtr`します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                      | 説明
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptr::as](#as)                                         | 返します、`ComPtr`指定されたテンプレート パラメーターで識別されるインターフェイスを表すオブジェクト。
[Comptr::asiid](#asiid)                                   | 返します、`ComPtr`指定したインターフェイス ID で識別されるインターフェイスを表すオブジェクトを
[Comptr::asweak](#asweak)                                 | 現在のオブジェクトへの弱い参照を取得します。
[Comptr::attach](#attach)                                 | これを関連付けます`ComPtr`現在のテンプレート型パラメーターで指定したインターフェイス型にします。
[ComPtr::CopyTo](#copyto)                                 | これに関連付けられている現在または指定されたインターフェイスのコピー`ComPtr`への指定された出力ポインター。
[Comptr::detach](#detach)                                 | この関連付けを解除`ComPtr`それが表すインターフェイスから。
[Comptr::get](#get)                                       | これに関連付けられているインターフェイスへのポインターを取得します。`ComPtr`します。
[Comptr::getaddressof](#getaddressof)                     | アドレスを取得、 [ptr _](#ptr)データ メンバーは、これによって表されるインターフェイスへのポインターを含む`ComPtr`します。
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | これに関連付けられているインターフェイスを解放`ComPtr`しのアドレスを取得し、 [ptr _](#ptr)データ メンバーは、リリースされたインターフェイスへのポインターが含まれています。
[ComPtr::Reset](#reset)                                   | これに関連付けられているインターフェイス ポインターのすべての参照を解放`ComPtr`します。
[Comptr::swap](#swap)                                     | 現在の管理インターフェイスを交換`ComPtr`、指定した管理インターフェイスで`ComPtr`します。

### <a name="protected-methods"></a>プロテクト メソッド

名前                                        | 説明
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | これに関連付けられているインターフェイスの参照カウントをインクリメント`ComPtr`します。
[ComPtr::InternalRelease](#internalrelease) | これに関連付けられているインターフェイスで COM 解放操作を行います`ComPtr`します。

### <a name="public-operators"></a>パブリック演算子

名前                                                                                           | 説明
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | 現在のアドレスを取得`ComPtr`します。
[ComPtr::operator->](#operator-arrow)                                                          | 現在のテンプレート パラメーターで指定された型へのポインターを取得します。
[Comptr::operator =](#operator-assign)                                                          | 現在の値を代入`ComPtr`します。
[ComPtr::operator==](#operator-equality)                                                       | 2 つの `ComPtr` オブジェクトが等しいかどうかを示します。
[Comptr::operator! =](#operator-inequality)                                                     | 2 つの `ComPtr` オブジェクトが等しくないかどうかを示します。
[Comptr::operator:booltype](#operator-microsoft-wrl-details-booltype) | 示すかどうかを`ComPtr`インターフェイスのオブジェクトの有効期間を管理します。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                 | 説明
-------------------- | ------------------------------------------------------------------------------------------
[Comptr::ptr _](#ptr) | 使用すると、関連付けられているされ、これによって管理されるインターフェイスへのポインターを含む`ComPtr`します。

## <a name="inheritance-hierarchy"></a>継承階層

`ComPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

**名前空間:** Microsoft::wrl

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

インスタンスを初期化解除`ComPtr`します。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>Comptr::as

返します、`ComPtr`指定されたテンプレート パラメーターで識別されるインターフェイスを表すオブジェクト。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>パラメーター

*U*<br/>
パラメーターで表されるインターフェイス*p*します。

*p*<br/>
A`ComPtr`パラメーターで指定されたインターフェイスを表すオブジェクトを*U*します。パラメーター *p*現在を指していない`ComPtr`オブジェクト。

### <a name="remarks"></a>Remarks

最初のテンプレートは、コードで使用する必要があるフォームです。 2 番目のテンプレートは、 [auto](../../cpp/auto-cpp.md) 型推論キーワードなどの C++ 言語の機能をサポートしている内部ヘルパーの特殊化です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="asiid"></a>Comptr::asiid

返します、`ComPtr`指定したインターフェイス ID で識別されるインターフェイスを表すオブジェクトを

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*p*<br/>
オブジェクトのインターフェイス ID を持つと等しい場合*riid*で指定されたインターフェイスを二重間接ポインター、 *riid*パラメーター、それ以外へのポインター`IUnknown`します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="asweak"></a>Comptr::asweak

現在のオブジェクトへの弱い参照を取得します。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>パラメーター

*pWeakRef*<br/>
この操作が完了時は、弱い参照オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="attach"></a>Comptr::attach

これを関連付けます`ComPtr`現在のテンプレート型パラメーターで指定したインターフェイス型にします。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>パラメーター

*other*<br/>
インターフェイスの型。

## <a name="comptr"></a>Comptr::comptr

`ComPtr` クラスの新しいインスタンスを初期化します。 オーバーロードは、既定、コピー、移動、および変換の各コンストラクターを提供します。

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>パラメーター

*U*<br/>
種類、*他*パラメーター。

*other*<br/>
型のオブジェクト*U*します。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

最初のコンス トラクターは、どの暗黙的は、空のオブジェクトを作成します。 既定のコンス トラクターです。 2 番目のコンス トラクターを指定します[_ _nullptr](../nullptr-cpp-component-extensions.md)を明示的に空のオブジェクトを作成します。

3 番目のコンス トラクターは、ポインターで指定されたオブジェクトからオブジェクトを作成します。

4 番目と 5 番目のコンス トラクターは、コピー コンス トラクターです。 5 番目のコンス トラクターは、現在の型に変換可能である場合、オブジェクトをコピーします。

6 番目と 7 番目のコンス トラクターは、移動コンス トラクターです。 7 番目のコンス トラクターは、現在の型に変換可能である場合、オブジェクトを移動します。

## <a name="copyto"></a>ComPtr::CopyTo

これに関連付けられている現在または指定されたインターフェイスのコピー`ComPtr`へのポインターを指定します。

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>パラメーター

*U*<br/>
型の名前。

*ptr*<br/>
この操作が完了時は、要求されたインターフェイスへのポインター。

*riid*<br/>
インターフェイス ID。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、その理由を示す HRESULT 暗黙`QueryInterface`操作に失敗しました。

### <a name="remarks"></a>Remarks

最初の関数は、これに関連付けられているインターフェイスへのポインターのコピーを返します`ComPtr`します。 この関数は、常に S_OK を返します。

2 番目の関数の実行、`QueryInterface`これに関連付けられているインターフェイスで操作`ComPtr`で指定されたインターフェイスの*riid*パラメーター。

3 番目の関数の実行、`QueryInterface`これに関連付けられているインターフェイスで操作`ComPtr`の基になるインターフェイスの*U*パラメーター。

## <a name="detach"></a>Comptr::detach

この関連付けを解除`ComPtr`それが表すインターフェイスからのオブジェクト。

```cpp
T* Detach();
```

### <a name="return-value"></a>戻り値

これによって表されるインターフェイスへのポインター`ComPtr`オブジェクト。

## <a name="get"></a>Comptr::get

これに関連付けられているインターフェイスへのポインターを取得します。`ComPtr`します。

```cpp
T* Get() const;
```

### <a name="return-value"></a>戻り値

これに関連付けられているインターフェイスへのポインター`ComPtr`します。

## <a name="getaddressof"></a>Comptr::getaddressof

アドレスを取得、 [ptr _](#ptr)データ メンバーは、これによって表されるインターフェイスへのポインターを含む`ComPtr`します。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>戻り値

変数のアドレス。

## <a name="internaladdref"></a>ComPtr::InternalAddRef

これに関連付けられているインターフェイスの参照カウントをインクリメント`ComPtr`します。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Remarks

このメソッドは保護されます。

## <a name="internalrelease"></a>Comptr::internalrelease

これに関連付けられているインターフェイスで COM 解放操作を行います`ComPtr`します。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Remarks

このメソッドは保護されます。

## <a name="operator-ampersand"></a>Comptr::operator&amp;

これに関連付けられているインターフェイスを解放`ComPtr`オブジェクトし、のアドレスを取得し、`ComPtr`オブジェクト。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>戻り値

現在への弱い参照`ComPtr`します。

### <a name="remarks"></a>Remarks

このメソッドが異なる[comptr::getaddressof](#getaddressof)ことで、このメソッドは、インターフェイス ポインターへの参照を解放します。 使用`ComPtr::GetAddressOf`インターフェイス ポインターのアドレスが必要ですが、そのインターフェイスを解放したくないです。

## <a name="operator-arrow"></a>Comptr::operator-&gt;

現在のテンプレート パラメーターで指定された型へのポインターを取得します。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>戻り値

現在のテンプレート型名で指定された型へのポインター。

### <a name="remarks"></a>Remarks

このヘルパー関数は、STDMETHOD マクロを使用することで、不要なオーバーヘッドを削除します。 この関数は、`IUnknown`型`private`の代わりに`virtual`します。

## <a name="operator-assign"></a>Comptr::operator =

現在の値を代入`ComPtr`します。

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>パラメーター

*U*<br/>
クラス。

*other*<br/>
ポインター、参照、または右辺値参照型または別に`ComPtr`します。

### <a name="return-value"></a>戻り値

現在への参照を`ComPtr`します。

### <a name="remarks"></a>Remarks

この演算子の最初のバージョンは現在空の値を割り当てます`ComPtr`します。

2 番目のバージョンでは、割り当てのインターフェイス ポインターでない現在のと同じ場合`ComPtr`インターフェイス ポインターの場合は、2 番目のインターフェイス ポインターが現在割り当てられている`ComPtr`します。

現在の 3 番目のバージョンでは、割り当てのインターフェイス ポインターが割り当てられている`ComPtr`します。

4 番目のバージョンでは、割り当ての値のインターフェイス ポインターでない現在のと同じ場合`ComPtr`インターフェイス ポインターの場合は、2 番目のインターフェイス ポインターが現在割り当てられている`ComPtr`します。

5 番目のバージョンがコピー演算子です。参照を`ComPtr`に現在割り当てられている`ComPtr`します。

6 番目のバージョンを使用するコピー操作は、移動セマンティクスです。右辺値参照を`ComPtr`キャストし、現在割り当てられている、任意の型が静的な場合`ComPtr`します。

7 番目のバージョンを使用するコピー操作は、移動セマンティクスです。右辺値参照を`ComPtr`型の*U*は静的キャストしとに現在割り当てられている`ComPtr`します。

## <a name="operator-equality"></a>Comptr::operator = =

2 つの `ComPtr` オブジェクトが等しいかどうかを示します。

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>パラメーター

*a*<br/>
`ComPtr` オブジェクトへの参照。

*b*<br/>
別の参照`ComPtr`オブジェクト。

### <a name="return-value"></a>戻り値

最初の演算子と`true`場合オブジェクト *、* がオブジェクトと等しい*b*、それ以外の`false`します。

2 番目と 3 番目の演算子を生成`true`場合オブジェクト *、* と等しい`nullptr`、それ以外の`false`します。

## <a name="operator-inequality"></a>Comptr::operator! =

2 つの `ComPtr` オブジェクトが等しくないかどうかを示します。

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>パラメーター

*a*<br/>
`ComPtr` オブジェクトへの参照。

*b*<br/>
別の参照`ComPtr`オブジェクト。

### <a name="return-value"></a>戻り値

最初の演算子と`true`場合オブジェクト *、* オブジェクトと等しくない*b*、それ以外の`false`します。

2 番目と 3 番目の演算子を生成`true`場合オブジェクト *、* が等しくない`nullptr`、それ以外の`false`します。

## <a name="operator-microsoft-wrl-details-booltype"></a>Comptr::operator:booltype

示すかどうかを`ComPtr`インターフェイスのオブジェクトの有効期間を管理します。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>戻り値

インターフェイスに関連付けられている場合`ComPtr`のアドレス、 [boolstruct::member](boolstruct-structure.md#member)データ メンバー、それ以外の`nullptr`します。

## <a name="ptr"></a>Comptr::ptr _

使用すると、関連付けられているされ、これによって管理されるインターフェイスへのポインターを含む`ComPtr`します。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Remarks

`ptr_` 内部の保護されたデータ メンバーです。

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

これに関連付けられているインターフェイスを解放`ComPtr`しのアドレスを取得し、 [ptr _](#ptr)データ メンバーは、リリースされたインターフェイスへのポインターが含まれています。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>戻り値

アドレス、 [ptr _](#ptr)データ メンバー`ComPtr`します。

## <a name="reset"></a>ComPtr::Reset

これに関連付けられているインターフェイス ポインターのすべての参照を解放`ComPtr`します。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>戻り値

解放された参照の数 (存在する場合)。

## <a name="swap"></a>Comptr::swap

現在の管理インターフェイスを交換`ComPtr`、指定した管理インターフェイスで`ComPtr`します。

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>パラメーター

*r*<br/>
`ComPtr`。

