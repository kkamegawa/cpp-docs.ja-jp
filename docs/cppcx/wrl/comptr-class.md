---
title: ComPtr クラス
ms.date: 07/26/2019
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
ms.openlocfilehash: 1e20a991c8f32027aeea6a17df0534aa6e1c2c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498414"
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
が`ComPtr`表すインターフェイス。

*U*<br/>
現在`ComPtr`のがフレンドであるクラス。 (このパラメーターを使用するテンプレートは保護されています)。

## <a name="remarks"></a>Remarks

`ComPtr<>`基になるインターフェイスポインターを表す型を宣言します。 を`ComPtr<>`使用して変数を宣言し、矢印のメンバーアクセス演算子 (`->`) を使用してインターフェイスメンバー関数にアクセスします。

スマートポインターの詳細については、MSDN ライブラリの[Com コーディング方法](/windows/win32/LearnWin32/com-coding-practices)に関するトピックの「Com スマートポインター」サブセクションを参照してください。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前            | 説明
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*テンプレートパラメーターによって指定された型のシノニム。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                             | 説明
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | `ComPtr` クラスの新しいインスタンスを初期化します。 オーバーロードは、既定、コピー、移動、および変換の各コンストラクターを提供します。
[ComPtr:: ~ ComPtr](#tilde-comptr) | の`ComPtr`インスタンスを初期化解除します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                      | 説明
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: As](#as)                                         | 指定されたテンプレートパラメーターで識別されるインターフェイスを表すオブジェクトを返します。`ComPtr`
[ComPtr:: AsIID](#asiid)                                   | 指定したインターフェイス ID によって識別されるインターフェイスを表すオブジェクトを返します。`ComPtr`
[ComPtr:: AsWeak](#asweak)                                 | 現在のオブジェクトへの弱い参照を取得します。
[ComPtr:: Attach](#attach)                                 | この`ComPtr`を、現在のテンプレート型パラメーターで指定されたインターフェイス型に関連付けます。
[ComPtr:: CopyTo](#copyto)                                 | この`ComPtr`に関連付けられている現在のまたは指定されたインターフェイスを、指定した出力ポインターにコピーします。
[Comptr::D etcomp](#detach)                                 | この`ComPtr`と、それが表すインターフェイスとの関連付けを解除します。
[ComPtr:: Get](#get)                                       | この`ComPtr`に関連付けられているインターフェイスへのポインターを取得します。
[ComPtr:: GetAddressOf](#getaddressof)                     | この`ComPtr`によって表されるインターフェイスへのポインターを含む[ptr_](#ptr)データメンバーのアドレスを取得します。
[ComPtr:: ReleaseAndGetAddressOf](#releaseandgetaddressof) | このに関連付けられ`ComPtr`ているインターフェイスを解放し、 [ptr_](#ptr)データメンバーのアドレスを取得します。このアドレスには、解放されたインターフェイスへのポインターが含まれています。
[ComPtr::Reset](#reset)                                   | この`ComPtr`に関連付けられているインターフェイスへのポインターのすべての参照を解放します。
[ComPtr:: Swap](#swap)                                     | 現在`ComPtr`のによって管理されているインターフェイスと、指定`ComPtr`したによって管理されるインターフェイスを交換します。

### <a name="protected-methods"></a>プロテクト メソッド

名前                                        | 説明
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | この`ComPtr`に関連付けられているインターフェイスの参照カウントをインクリメントします。
[ComPtr:: InternalRelease](#internalrelease) | この`ComPtr`に関連付けられているインターフェイスに対して COM 解放操作を実行します。

### <a name="public-operators"></a>パブリック演算子

名前                                                                                           | 説明
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | 現在`ComPtr`ののアドレスを取得します。
[ComPtr:: operator->](#operator-arrow)                                                          | 現在のテンプレート パラメーターで指定された型へのポインターを取得します。
[ComPtr:: operator =](#operator-assign)                                                          | 現在`ComPtr`のに値を割り当てます。
[ComPtr:: operator = =](#operator-equality)                                                       | 2 つの `ComPtr` オブジェクトが等しいかどうかを示します。
[ComPtr:: operator! =](#operator-inequality)                                                     | 2 つの `ComPtr` オブジェクトが等しくないかどうかを示します。
[ComPtr:: operator Microsoft:: WRL::D etails:: ブール型](#operator-microsoft-wrl-details-booltype) | `ComPtr`がインターフェイスのオブジェクトの有効期間を管理しているかどうかを示します。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                 | 説明
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | このに関連付けられ、この`ComPtr`によって管理されるインターフェイスへのポインターを格納します。

## <a name="inheritance-hierarchy"></a>継承階層

`ComPtr`

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

**名前空間:** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

の`ComPtr`インスタンスを初期化解除します。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: As

指定されたテンプレートパラメーターで識別されるインターフェイスを表すオブジェクトを返します。`ComPtr`

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
パラメーター *p*で表されるインターフェイス。

*p*<br/>
パラメーター *U*によって指定されたインターフェイスを表すオブジェクト。`ComPtr`パラメーター *p*で現在`ComPtr`のオブジェクトを参照することはできません。

### <a name="remarks"></a>Remarks

最初のテンプレートは、コードで使用する必要があるフォームです。 2 番目のテンプレートは、 [auto](../../cpp/auto-cpp.md) 型推論キーワードなどの C++ 言語の機能をサポートしている内部ヘルパーの特殊化です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="asiid"></a>ComPtr:: AsIID

指定したインターフェイス ID によって識別されるインターフェイスを表すオブジェクトを返します。`ComPtr`

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
オブジェクトに ID が*riid*であるインターフェイスがある場合は、 *riid*パラメーターによって指定されたインターフェイスへの二重間接ポインターです。それ以外の場合は`IUnknown`、へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="asweak"></a>ComPtr:: AsWeak

現在のオブジェクトへの弱い参照を取得します。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>パラメーター

*pWeakRef*<br/>
この操作が完了したときに、弱い参照オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="attach"></a>ComPtr:: Attach

この`ComPtr`を、現在のテンプレート型パラメーターで指定されたインターフェイス型に関連付けます。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>パラメーター

*other*<br/>
インターフェイス型。

## <a name="comptr"></a>ComPtr:: ComPtr

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
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>パラメーター

*U*<br/>
*もう一方*のパラメーターの型。

*other*<br/>
*U*型のオブジェクト。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

最初のコンストラクターは既定のコンストラクターで、暗黙的は空のオブジェクトを作成します。 2番目のコンストラクターは、空のオブジェクトを明示的に作成する[__ nullptr](../../extensions/nullptr-cpp-component-extensions.md)を指定します。

3番目のコンストラクターは、ポインターによって指定されたオブジェクトからオブジェクトを作成します。 ComPtr は、ポイントされたメモリを所有し、それに対する参照カウントを保持するようになりました。

4番目と5番目のコンストラクターは、コピーコンストラクターです。 5番目のコンストラクターは、現在の型に変換できる場合にオブジェクトをコピーします。

6番目と7番目のコンストラクターは移動コンストラクターです。 7番目のコンストラクターは、現在の型に変換できる場合にオブジェクトを移動します。

## <a name="copyto"></a>ComPtr:: CopyTo

この`ComPtr`に関連付けられている現在のまたは指定されたインターフェイスを、指定したポインターにコピーします。

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
この操作が完了したときに、要求されたインターフェイスへのポインター。

*riid*<br/>
インターフェイス ID。

### <a name="return-value"></a>戻り値

成功した場合は S_OK。それ以外の場合は、暗黙的`QueryInterface`な操作が失敗した理由を示す HRESULT。

### <a name="remarks"></a>Remarks

最初の関数は、この`ComPtr`に関連付けられているインターフェイスへのポインターのコピーを返します。 この関数は常に S_OK を返します。

2番目の関数`QueryInterface`は、この`ComPtr`に関連付けられているインターフェイスに対して、 *riid*パラメーターによって指定されたインターフェイスに対して操作を実行します。

3番目の関数`QueryInterface`は、この`ComPtr`に関連付けられているインターフェイスに対して、 *U*パラメーターの基になるインターフェイスに対して操作を実行します。

## <a name="detach"></a>Comptr::D etcomp

この`ComPtr`オブジェクトと、それが表すインターフェイスとの関連付けを解除します。

```cpp
T* Detach();
```

### <a name="return-value"></a>戻り値

この`ComPtr`オブジェクトによって表されるインターフェイスへのポインター。

## <a name="get"></a>ComPtr:: Get

この`ComPtr`に関連付けられているインターフェイスへのポインターを取得します。

```cpp
T* Get() const;
```

### <a name="return-value"></a>戻り値

この`ComPtr`に関連付けられているインターフェイスへのポインター。

## <a name="getaddressof"></a>ComPtr:: GetAddressOf

この`ComPtr`によって表されるインターフェイスへのポインターを含む[ptr_](#ptr)データメンバーのアドレスを取得します。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>戻り値

変数のアドレス。

## <a name="internaladdref"></a>ComPtr:: InternalAddRef

この`ComPtr`に関連付けられているインターフェイスの参照カウントをインクリメントします。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Remarks

このメソッドは保護されています。

## <a name="internalrelease"></a>ComPtr:: InternalRelease

この`ComPtr`に関連付けられているインターフェイスに対して COM 解放操作を実行します。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Remarks

このメソッドは保護されています。

## <a name="operator-ampersand"></a>ComPtr:: operator&amp;

この`ComPtr`オブジェクトに関連付けられているインターフェイスを解放し、 `ComPtr`オブジェクトのアドレスを取得します。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>戻り値

現在`ComPtr`のへの弱い参照。

### <a name="remarks"></a>Remarks

このメソッドは、インターフェイスポインターへの参照を解放するという点で、 [Comptr:: GetAddressOf](#getaddressof)とは異なります。 インターフェイス`ComPtr::GetAddressOf`ポインターのアドレスが必要であるものの、そのインターフェイスを解放しない場合は、を使用します。

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

現在のテンプレート パラメーターで指定された型へのポインターを取得します。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>戻り値

現在のテンプレートの型名によって指定された型へのポインター。

### <a name="remarks"></a>Remarks

このヘルパー関数は、STDMETHOD マクロを使用することによって生じる不要なオーバーヘッドを除去します。 この関数`IUnknown`は、では`virtual`なく型`private`を作成します。

## <a name="operator-assign"></a>ComPtr:: operator =

現在`ComPtr`のに値を割り当てます。

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
型または別`ComPtr`の型へのポインター、参照、または右辺値参照。

### <a name="return-value"></a>戻り値

現在`ComPtr`のへの参照。

### <a name="remarks"></a>Remarks

この演算子の最初のバージョンでは、現在`ComPtr`のに空の値が割り当てられます。

2番目のバージョンでは、割り当てインターフェイスポインターが現在`ComPtr`のインターフェイスポインターと同じでない場合、2番目のインターフェイスポインターが現在`ComPtr`のに割り当てられます。

3番目のバージョンでは、割り当てインターフェイスポインターが現在`ComPtr`のに割り当てられます。

4番目のバージョンでは、割り当て値のインターフェイスポインターが現在`ComPtr`のインターフェイスポインターと同じでない場合、2番目のインターフェイスポインターが現在`ComPtr`のに割り当てられます。

5番目のバージョンは、コピー演算子です。へ`ComPtr`の参照が現在`ComPtr`のに割り当てられています。

6番目のバージョンは、移動セマンティクスを使用するコピー演算子です。任意の型が静的`ComPtr`キャストであり、現在`ComPtr`のに割り当てられている場合は、への右辺値参照。

7番目のバージョンは、移動セマンティクスを使用するコピー演算子です。`ComPtr` *U*型のへの右辺値参照は、静的キャストであり、現在`ComPtr`のに割り当てられています。

## <a name="operator-equality"></a>ComPtr:: operator = =

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
別`ComPtr`のオブジェクトへの参照。

### <a name="return-value"></a>戻り値

最初の演算子は`true` 、オブジェクト*a*がオブジェクト*b*と等しい場合はを`false`生成します。それ以外の場合はを返します。

2番目と3番`true`目の演算子は、オブジェクト`nullptr` *a*がと`false`等しい場合はを、それ以外の場合はを生成します。

## <a name="operator-inequality"></a>ComPtr:: operator! =

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
別`ComPtr`のオブジェクトへの参照。

### <a name="return-value"></a>戻り値

最初の演算子は`true` 、オブジェクト*a*がオブジェクト*b*と等しくない場合はを`false`、それ以外の場合はを生成します。

2番目と3番`true`目の演算子は、オブジェクト*a* `nullptr`がと等しく`false`ない場合はを、それ以外の場合はを生成します。

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: ブール型

`ComPtr`がインターフェイスのオブジェクトの有効期間を管理しているかどうかを示します。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>戻り値

インターフェイスがこの`ComPtr`に関連付けられている場合は、 [bool struct:: Member](boolstruct-structure.md#member)データメンバーのアドレス`nullptr`。それ以外の場合は。

## <a name="ptr"></a>ComPtr::p tr_

このに関連付けられ、この`ComPtr`によって管理されるインターフェイスへのポインターを格納します。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Remarks

`ptr_`は、保護された内部のデータメンバーです。

## <a name="releaseandgetaddressof"></a>ComPtr:: ReleaseAndGetAddressOf

このに関連付けられ`ComPtr`ているインターフェイスを解放し、 [ptr_](#ptr)データメンバーのアドレスを取得します。このアドレスには、解放されたインターフェイスへのポインターが含まれています。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>戻り値

この`ComPtr`の[ptr_](#ptr)データメンバーのアドレス。

## <a name="reset"></a>ComPtr:: Reset

この`ComPtr`に関連付けられているインターフェイスへのポインターのすべての参照を解放します。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>戻り値

解放された参照の数 (存在する場合)。

## <a name="swap"></a>ComPtr:: Swap

現在`ComPtr`のによって管理されているインターフェイスと、指定`ComPtr`したによって管理されるインターフェイスを交換します。

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

