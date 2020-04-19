---
title: ICommandImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: d890b62e4e4aabb9f8ca7ebb9d3051c53febd91f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408967"
---
# <a name="icommandimpl-class"></a>ICommandImpl クラス

実装を提供、 [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`ICommandImpl`します。

*CommandBase*<br/>
コマンド インターフェイスです。 既定値は `ICommand` です。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[キャンセル](#cancel)|現在のコマンドの実行をキャンセルします。|
|[CancelExecution](#cancelexecution)|現在のコマンドの実行をキャンセルします。|
|[CreateRowset](#createrowset)|行セット オブジェクトを作成します。|
|[Execute](#execute)|コマンドを実行します。|
|[GetDBSession](#getdbsession)|コマンドを作成したセッションにインターフェイス ポインターを返します。|
|[ICommandImpl](#icommandimpl)|コンストラクターです。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_bCancel](#bcancel)|コマンドが取り消されるかどうかを示します。|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|コマンドを実行中にキャンセルするかどうかを示します。|
|[m_bIsExecuting](#bisexecuting)|コマンドが現在実行されているかどうかを示します。|

## <a name="remarks"></a>Remarks

コマンド オブジェクトの必須インターフェイス。

## <a name="cancel"></a> ICommandImpl::Cancel

現在のコマンドの実行をキャンセルします。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Remarks

参照してください[icommand::cancel](/previous-versions/windows/desktop/ms714402(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="cancelexecution"></a> ICommandImpl::CancelExecution

現在のコマンドの実行をキャンセルします。

### <a name="syntax"></a>構文

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> ICommandImpl::CreateRowset

によって呼び出される[Execute](../../data/oledb/icommandimpl-execute.md)を 1 つの行セットを作成します。

### <a name="syntax"></a>構文

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>パラメーター

*RowsetClass*<br/>
ユーザーの行セット クラスを表すテンプレート クラスのメンバー。 通常、ウィザードによって生成されます。

*pUnkOuter*<br/>
[in]制御側へのポインター`IUnknown`インターフェイスの行セットが集計の一部として作成される場合は、それ以外の場合は null です。

*riid*<br/>
[in]対応する*riid*で`ICommand::Execute`します。

*pParams*<br/>
[入力/出力]対応する*pParams*で`ICommand::Execute`します。

*pcRowsAffected*<br/>
対応する*入力/出力*で`ICommand::Execute`します。

*ppRowset*<br/>
[入力/出力]対応する*ppRowset*で`ICommand::Execute`します。

*pRowsetObj*<br/>
[out]行セット オブジェクトへのポインター。 通常、このパラメーターは使用されませんが COM オブジェクトに渡す前に、行セットに対してより多くの作業を実行する必要がある場合に使用できます。 有効期間*pRowsetObj*連結された*ppRowset*します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。 参照してください`ICommand::Execute`の一般的な値の一覧についてはします。

### <a name="remarks"></a>Remarks

1 つ以上の行セットを作成するか、別の行セットを作成するための独自の条件を提供するには、別の呼び出しを配置`CreateRowset`内から`Execute`します。

参照してください[icommand::execute](/previous-versions/windows/desktop/ms718095(v=vs.85))で、 *OLE DB プログラマーズ リファレンス。*

## <a name="execute"></a> ICommandImpl::Execute

コマンドを実行します。

### <a name="syntax"></a>構文

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>パラメーター

参照してください[icommand::execute](/previous-versions/windows/desktop/ms718095(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

要求された発信インターフェイスは、この関数を作成する、行セット オブジェクトから取得したインターフェイスになります。

`Execute` 呼び出し[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)します。 1 つ以上の行セットを作成するか、別の行セットを作成するための独自の条件を提供する既定の実装をオーバーライドします。

## <a name="getdbsession"></a> ICommandImpl::GetDBSession

コマンドを作成したセッションにインターフェイス ポインターを返します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>パラメーター

参照してください[ICommand::GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

セッションからプロパティを取得するために便利です。

## <a name="icommandimpl"></a> ICommandImpl::ICommandImpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> ICommandImpl::m_bCancel

コマンドが取り消されたかどうかを示します。

### <a name="syntax"></a>構文

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Remarks

この変数を取得することができます、`Execute`コマンド クラスと適切なキャンセルのメソッド。

## <a name="bcancelwhenexecuting"></a> Icommandimpl::m_bcancelwhenexecuting

実行時にコマンドをキャンセルできるかどうかを示します。

### <a name="syntax"></a>構文

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Remarks

既定値は**true** (キャンセルできます)。

## <a name="bisexecuting"></a> ICommandImpl::m_bIsExecuting

コマンドが現在実行されているかどうかを示します。

### <a name="syntax"></a>構文

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Remarks

`Execute`コマンド クラスのメソッドでは、この変数に設定**true**します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)