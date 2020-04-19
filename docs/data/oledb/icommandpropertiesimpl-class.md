---
title: ICommandPropertiesImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: 1250f1c5c5094a0ca8348f325260e6079afe2baa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408954"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl クラス

実装を提供、 [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生クラス。

*PropClass*<br/>
プロパティ クラス。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[GetProperties](#getproperties)|行セットの現在要求されている行セット プロパティ グループ内のプロパティの一覧を返します。|
|[SetProperties](#setproperties)|行セット プロパティ グループのプロパティを設定します。|

## <a name="remarks"></a>Remarks

これは、コマンドでは必須です。 によって定義された静的関数によって提供される、実装、 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)マクロ。

## <a name="getproperties"></a> ICommandPropertiesImpl::GetProperties

コマンドのプロパティのマップを使用してすべての要求されたプロパティ セットが返されます。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandproperties::getproperties](/previous-versions/windows/desktop/ms723119(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

「 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)」を参照してください。

## <a name="setproperties"></a> ICommandPropertiesImpl::SetProperties

コマンド オブジェクトのプロパティを設定します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandproperties::setproperties](/previous-versions/windows/desktop/ms711497(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)