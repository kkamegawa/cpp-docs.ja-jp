---
title: RuntimeClass クラス
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: d45fe7c6d794f216da93ffbd95dbb7058d3336f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403192"
---
# <a name="runtimeclass-class"></a>RuntimeClass クラス

指定したインターフェイスを継承し、指定した Windows ランタイム、クラシック COM、および弱い参照のサポートを提供する WinRT または COM クラスを表します。

このクラスの実装を提供する、WinRT と COM クラスの定型実装を提供`QueryInterface`、 `AddRef`、`Release`など、モジュールの参照カウントを管理しのクラス ファクトリを提供するためのサポートアクティブ化可能なオブジェクト。

## <a name="syntax"></a>構文

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>パラメーター

*classFlags*<br/>
省略可能なパラメーターです。 1 つ以上を組み合わせた[RuntimeClassType](runtimeclasstype-enumeration.md)列挙値。 `__WRL_CONFIGURATION_LEGACY__` ClassFlags プロジェクト内のすべてのランタイム クラスの既定値を変更するマクロを定義することができます。 定義されている場合、RuntimeClass インスタンスは既定でアジャイルです。 定義されていないときに、RuntimeClass インスタンスは、既定でアジャイルです。 あいまいさを避けるために指定常に、`Microsoft::WRL::FtmBase`で`TInterfaces`または`RuntimeClassType::InhibitFtmBase`します。 InhibitFtmBase と FtmBase はどちらもオブジェクトを使用している場合は、アジャイルになります。

*TInterfaces*<br/>
インターフェイスの一覧を超えるオブジェクトが実装されて`IUnknown`、`IInspectable`または他のインターフェイスによって制御される[RuntimeClassType](runtimeclasstype-enumeration.md)します。 特にから派生するその他のクラス リストが`Microsoft::WRL::FtmBase`アジャイル オブジェクトを作成して実装するために、`IMarshal`します。

## <a name="members"></a>メンバー

`RuntimeClassInitialize`<br/>
場合、オブジェクトを初期化する関数、`MakeAndInitialize`テンプレート関数は、オブジェクトを構築するために使用します。 初期化に失敗した場合、オブジェクトが正常に初期化すると場合は、S_OK または COM エラー コードを返します。 戻り値として COM エラー コードが伝達される`MakeAndInitialize`します。 なお、`RuntimeClassInitialize`場合、メソッドは呼び出されません、`Make`テンプレート関数は、オブジェクトを構築するために使用します。

### <a name="public-constructors"></a>パブリック コンストラクター

| 名前                                               | 説明                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | 現在のインスタンスを初期化します、`RuntimeClass`クラス。   |
| [RuntimeClass::~RuntimeClass](#tilde-runtimeclass) | 現在のインスタンスの初期化を解除、`RuntimeClass`クラス。 |

### <a name="public-methods"></a>パブリック メソッド

| 名前                                                      | 説明                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | 現在の参照カウントをインクリメント`RuntimeClass`オブジェクト。                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | 参照が現在のカウントをデクリメント`RuntimeClass`オブジェクト。                              |
| [Runtimeclass::getiids](#getiids)                         | インターフェイス Id を現在の実装を含むことのできる配列を取得します`RuntimeClass`オブジェクト。 |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | 現在のランタイム クラス名を取得`RuntimeClass`オブジェクト。                                  |
| [Runtimeclass::gettrustlevel](#gettrustlevel)             | 現在の信頼レベルを取得`RuntimeClass`オブジェクト。                                         |
| [Runtimeclass::getweakreference](#getweakreference)       | 現在の弱い参照オブジェクトにポインターを取得します。`RuntimeClass`オブジェクト。                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | 現在の参照カウントをインクリメント`RuntimeClass`オブジェクト。                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | 指定したインターフェイス ID へのポインターを取得します。                                                 |
| [RuntimeClass::Release](#release)                         | 現在の COM 解放操作を実行します。`RuntimeClass`オブジェクト。                             |

## <a name="inheritance-hierarchy"></a>継承階層

これは、実装の詳細です。

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="tilde-runtimeclass"></a>RuntimeClass:: ~ RuntimeClass

現在のインスタンスの初期化を解除、`RuntimeClass`クラス。

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>RuntimeClass::AddRef

現在の参照カウントをインクリメント`RuntimeClass`オブジェクト。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="decrementreference"></a>RuntimeClass::DecrementReference

参照が現在のカウントをデクリメント`RuntimeClass`オブジェクト。

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="getiids"></a>RuntimeClass::GetIids

インターフェイス Id を現在の実装を含むことのできる配列を取得します`RuntimeClass`オブジェクト。

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>パラメーター

*iidCount*<br/>
ときにこの操作が完了すると、配列内の要素の合計数*iid*します。

*iid*<br/>
この操作が完了時は、インターフェイス Id の配列へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、E_OUTOFMEMORY します。

## <a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

現在のランタイム クラス名を取得`RuntimeClass`オブジェクト。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>パラメーター

*runtimeName*<br/>
この操作の完了時、ランタイム クラス名。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

場合は、アサート エラーが出力`__WRL_STRICT__`または`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`が定義されていません。

## <a name="gettrustlevel"></a>Runtimeclass::gettrustlevel

現在の信頼レベルを取得`RuntimeClass`オブジェクト。

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>パラメーター

*trustLvl*<br/>
ときにこの操作が完了すると、現在の信頼レベル`RuntimeClass`オブジェクト。

### <a name="return-value"></a>戻り値

常に s_ok を返します。

### <a name="remarks"></a>Remarks

場合は、アサート エラーが出力`__WRL_STRICT__`または`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`が定義されていません。

## <a name="getweakreference"></a>RuntimeClass::GetWeakReference

現在の弱い参照オブジェクトにポインターを取得します。`RuntimeClass`オブジェクト。

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>パラメーター

*weakReference*<br/>
この操作が完了時は、弱い参照オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

常に s_ok を返します。

## <a name="internaladdref"></a>RuntimeClass::InternalAddRef

現在の参照カウントをインクリメント`RuntimeClass`オブジェクト。

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>戻り値

結果として得られる、参照カウントします。

## <a name="queryinterface"></a>RuntimeClass::QueryInterface

指定したインターフェイス ID へのポインターを取得します。

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*ppvObject*<br/>
この opereation 完了時で指定されたインターフェイスへのポインター、 *riid*パラメーター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="release"></a>RuntimeClass::Release

現在の COM 解放操作を実行します。`RuntimeClass`オブジェクト。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

参照カウントが 0 になった場合、`RuntimeClass`オブジェクトを削除します。

## <a name="runtimeclass"></a>RuntimeClass::RuntimeClass

現在のインスタンスを初期化します、`RuntimeClass`クラス。

```cpp
RuntimeClass();
```
