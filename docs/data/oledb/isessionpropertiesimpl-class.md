---
title: ISessionPropertiesImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: ed8b7a271bc6ac234fc9276d6c88d26848da24f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390686"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl クラス

実装を提供、 [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`ISessionPropertiesImpl`します。

*PropClass*<br/>
その既定値はユーザー定義プロパティ クラス*T*します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[GetProperties](#getproperties)|セッションで現在設定されているセッション プロパティ グループ内のプロパティの一覧を返します。|
|[SetProperties](#setproperties)|セッション プロパティ グループのプロパティを設定します。|

## <a name="remarks"></a>Remarks

セッションの必須インターフェイス。 このクラスでは、セッションのプロパティを実装によって定義された静的関数を呼び出すことによって、[プロパティ セットのマップ](../../data/oledb/begin-propset-map.md)します。 セッション クラスでは、プロパティ セットのマップを指定する必要があります。

## <a name="getproperties"></a> ISessionPropertiesImpl::GetProperties

プロパティの一覧を返します、`DBPROPSET_SESSION`セッションで現在設定されているプロパティ グループ。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>パラメーター

参照してください[ISessionProperties::GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties

プロパティを設定、`DBPROPSET_SESSION`プロパティ グループ。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[ISessionProperties::SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)