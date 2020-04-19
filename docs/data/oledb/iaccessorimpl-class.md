---
title: IAccessorImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: a4f98cdfea9ea1e82ec0a3de09e292604a6c199f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409045"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl クラス

実装を提供、 [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
行セットまたはコマンドのオブジェクト クラス。

*BindType*<br/>
バインド情報のストレージ ユニット。 既定値は、`ATLBINDINGS`構造 (atldb.h を参照してください)。

*BindingVector*<br/>
列情報のストレージ ユニット。 既定値は[CAtlMap](../../atl/reference/catlmap-class.md) 、重要な要素は HACCESSOR 値を値要素へのポインター、`BindType`構造体。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|コンストラクターです。|

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|既存のアクセサーには、参照カウントを追加します。|
|[CreateAccessor](#createaccessor)|バインドのセットからアクセサーを作成します。|
|[GetBindings](#getbindings)|アクセサーのバインディングを返します。|
|[ReleaseAccessor](#releaseaccessor)|アクセサーを解放します。|

## <a name="remarks"></a>Remarks

これは、機能は、行セットおよびコマンドに必須です。 OLE DB、HACCESSOR を実装するプロバイダーを必要とタグの配列をある[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))構造体。 によって提供される HACCESSORs`IAccessorImpl`のアドレス、`BindType`構造体。 既定では、`BindType`として定義されている場合は、`ATLBINDINGS`で`IAccessorImpl`のテンプレートの定義。 `BindType` 使用されるメカニズムを提供します。`IAccessorImpl`内の要素の数を追跡するためにその`DBBINDING`参照カウントおよびアクセサーのフラグと配列。

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

既存のアクセサーには、参照カウントを追加します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>パラメーター

参照してください[IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

バインドのセットからアクセサーを作成します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>パラメーター

参照してください[iaccessor::createaccessor](/previous-versions/windows/desktop/ms720969(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="getbindings"></a> IAccessorImpl::GetBindings

アクセサーのコンシューマーからの列の基本的なバインディングを返します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>パラメーター

参照してください[IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

アクセサーを解放します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>パラメーター

参照してください[iaccessor::releaseaccessor](/previous-versions/windows/desktop/ms719717(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)