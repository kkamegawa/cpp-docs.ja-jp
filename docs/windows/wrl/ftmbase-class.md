---
title: FtmBase クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: fb7f103d8ea647f554d9bbf26c2e218d34f6b1ff
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336453"
---
# <a name="ftmbase-class"></a>FtmBase クラス

フリー スレッド マーシャラー オブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [RuntimeClass クラス](runtimeclass-class.md)します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

| 名前                         | 説明                                        |
| ---------------------------- | -------------------------------------------------- |
| [Ftmbase::ftmbase](#ftmbase) | `FtmBase` クラスの新しいインスタンスを初期化します。 |

### <a name="public-methods"></a>パブリック メソッド

| 名前                                                               | 説明                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Ftmbase::createglobalinterfacetable](#createglobalinterfacetable) | グローバル インターフェイス テーブル (GIT) を作成します。                                                                                                                              |
| [Ftmbase::disconnectobject](#disconnectobject)                     | オブジェクトへのすべての外部接続が強制的に解放します。 オブジェクトのサーバーでは、シャット ダウンする前に、このメソッドのオブジェクトの実装を呼び出します。                |
| [Ftmbase::getmarshalsizemax](#getmarshalsizemax)                   | 指定したオブジェクトで指定されたインターフェイス ポインターをマーシャ リングするために必要なバイト数の上限を取得します。                                                |
| [Ftmbase::getunmarshalclass](#getunmarshalclass)                   | COM を使用して、対応するプロキシのコードを含む DLL を検索する CLSID を取得します。 COM は初期化されていないプロキシのインスタンスを作成するには、この DLL を読み込みます。 |
| [Ftmbase::marshalinterface](#marshalinterface)                     | 一部のクライアント プロセスで、プロキシ オブジェクトを初期化するために必要なデータをストリームに書き込みます。                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | データのマーシャ リングされたパケットは破棄されます。                                                                                                                                    |
| [Ftmbase::unmarshalinterface](#unmarshalinterface)                 | 新しく作成されたプロキシを初期化し、そのプロキシにインターフェイス ポインターを返します。                                                                                    |

### <a name="public-data-members"></a>パブリック データ メンバー

| 名前                                | 説明                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Ftmbase::marshaller _](#marshaller) | フリー スレッド マーシャラーへの参照を保持します。 |

## <a name="inheritance-hierarchy"></a>継承階層

`FtmBase`

## <a name="requirements"></a>必要条件

**ヘッダー:** ftm.h

**名前空間:** Microsoft::wrl

## <a name="createglobalinterfacetable"></a>Ftmbase::createglobalinterfacetable

グローバル インターフェイス テーブル (GIT) を作成します。

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>パラメーター

*git*<br/>
この操作が完了時は、グローバル インターフェイス テーブルへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。、`IGlobalInterfaceTable`でトピック、`COM Interfaces`のサブトピック、 `COM Reference` MSDN ライブラリの「します。

## <a name="disconnectobject"></a>Ftmbase::disconnectobject

オブジェクトへのすべての外部接続が強制的に解放します。 オブジェクトのサーバーでは、シャット ダウンする前に、このメソッドのオブジェクトの実装を呼び出します。

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>パラメーター

*dwReserved*<br/>
今後使用するために予約されています。0 にする必要があります。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="ftmbase"></a>Ftmbase::ftmbase

`FtmBase` クラスの新しいインスタンスを初期化します。

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>Ftmbase::getmarshalsizemax

指定したオブジェクトで指定されたインターフェイス ポインターをマーシャ リングするために必要なバイト数の上限を取得します。

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
マーシャ リングするインターフェイスの識別子への参照。

*現在価値*<br/>
インターフェイス ポインターをマーシャ リングします。NULL にすることができます。

*dwDestContext*<br/>
コピー先のコンテキストが指定されたインターフェイスのマーシャ リングできない位置。

1 つまたは複数の MSHCTX 列挙値を指定します。

現時点では、マーシャ リング解除発生する可能性が現在のプロセス (MSHCTX_INPROC) の別のアパートメントまたは現在のプロセス (MSHCTX_LOCAL) と同じコンピューター上の別のプロセスでします。

*pvDestContext*<br/>
今後使用するために予約されていますNULL にする必要があります。

*mshlflags*<br/>
マーシャ リングするデータがクライアント プロセスに送信されるかどうかを示すフラグ: 一般的なケース、または複数のクライアントで取得できる、グローバル テーブルに書き込まれます。 1 つまたは複数の MSHLFLAGS 列挙値を指定します。

*pSize*<br/>
この操作が完了時は、マーシャ リングのストリームに書き込まれるデータの量に上限へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、または E_NOINTERFACE E_FAIL します。

## <a name="getunmarshalclass"></a>Ftmbase::getunmarshalclass

COM を使用して、対応するプロキシのコードを含む DLL を検索する CLSID を取得します。 COM は初期化されていないプロキシのインスタンスを作成するには、この DLL を読み込みます。

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
マーシャ リングするインターフェイスの識別子への参照。

*現在価値*<br/>
マーシャ リングする; インターフェイスへのポインター呼び出し元では、必要なインターフェイスには、ポインターにいない場合、NULL を指定できます。

*dwDestContext*<br/>
コピー先のコンテキストが指定されたインターフェイスのマーシャ リングできない位置。

1 つまたは複数の MSHCTX 列挙値を指定します。

マーシャ リング解除は、現在のプロセス (MSHCTX_INPROC) の別のアパートメントまたは現在のプロセス (MSHCTX_LOCAL) と同じコンピューター上の別のプロセスで発生します。

*pvDestContext*<br/>
今後使用するために予約されていますNULL にする必要があります。

*mshlflags*<br/>
この操作が完了時は、クライアント プロセスで、プロキシの作成に使用する、CLSID へのポインター。

*pCid*

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、s_false を返します。

## <a name="marshalinterface"></a>Ftmbase::marshalinterface

一部のクライアント プロセスで、プロキシ オブジェクトを初期化するために必要なデータをストリームに書き込みます。

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>パラメーター

*pStm*<br/>
マーシャ リング中に使用するストリームへのポインター。

*riid*<br/>
マーシャ リングするインターフェイスの識別子への参照。 このインターフェイスから派生する必要があります、`IUnknown`インターフェイス。

*現在価値*<br/>
マーシャ リング; へのインターフェイス ポインターへのポインター呼び出し元では、必要なインターフェイスには、ポインターにいない場合、NULL を指定できます。

*dwDestContext*<br/>
コピー先のコンテキストが指定されたインターフェイスのマーシャ リングできない位置。

1 つまたは複数の MSHCTX 列挙値を指定します。

マーシャ リング解除は、現在のプロセス (MSHCTX_INPROC) の別のアパートメントまたは (MSHCTX_LOCAL) の現在のプロセスと同じコンピューター上の別のプロセスでが発生することができます。

*pvDestContext*<br/>
今後使用するために予約されています。0 にする必要があります。

*mshlflags*<br/>
マーシャ リングするデータがクライアント プロセスに送信されるかどうかを指定します: 一般的なケース、または複数のクライアントで取得できる、グローバル テーブルに書き込まれます。

### <a name="return-value"></a>戻り値

インターフェイス ポインターが正常にマーシャ リング s_ok を返します。

E_NOINTERFACE、指定したインターフェイスがサポートされていません。

STG_E_MEDIUMFULL ストリームがいっぱいです。

E_FAIL、操作が失敗しました。

## <a name="marshaller"></a>Ftmbase::marshaller _

フリー スレッド マーシャラーへの参照を保持します。

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

データのマーシャ リングされたパケットは破棄されます。

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>パラメーター

*pStm*<br/>
破棄するデータ パケットを格納するストリームへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

## <a name="unmarshalinterface"></a>Ftmbase::unmarshalinterface

新しく作成されたプロキシを初期化し、そのプロキシにインターフェイス ポインターを返します。

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>パラメーター

*pStm*<br/>
インターフェイス ポインターのマーシャ リングする元となるストリームへのポインター。

*riid*<br/>
マーシャ リングするインターフェイスの識別子への参照。

*ppv*<br/>
ときにこの操作が完了したらで要求されたインターフェイス ポインターを受け取るポインター変数のアドレス*riid*します。 この操作が成功した場合 **ppv*マーシャ リングするインターフェイスの要求されたインターフェイス ポインターが含まれています。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、または E_FAIL E_NOINTERFACE します。
