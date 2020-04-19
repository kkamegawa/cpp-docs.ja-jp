---
title: IDBCreateCommandImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 7450d91cd5e5383b55e2ebb391fe5f1190cbed2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408915"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl クラス

実装を提供、 [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>パラメーター

*T*<br/>
セッション オブジェクトから派生した`IDBCreateCommandImpl`します。

*CommandClass*<br/>
コマンド クラス。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[CreateCommand](#createcommand)|新しいコマンドを作成します。|

## <a name="remarks"></a>Remarks

新しいコマンドを取得するセッション オブジェクトの省略可能なインターフェイスです。

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand

新しいコマンドを作成し、要求されたインターフェイスを返します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>パラメーター

参照してください[idbcreatecommand::createcommand](/previous-versions/windows/desktop/ms709772(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

いくつかのパラメーターに対応*OLE DB プログラマーズ リファレンス*で説明されている別の名前のパラメーター `IDBCreateCommand::CreateCommand`:

|OLE DB テンプレート パラメーター|*OLE DB プログラマーズ リファレンス*パラメーター|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)