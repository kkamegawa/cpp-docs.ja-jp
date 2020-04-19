---
title: IDBInitializeImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 3418ce11e1a607d66fee593b32fd3a4b7d197407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409019"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl クラス

実装を提供、 [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`IDBInitializeImpl`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|コンストラクターです。|

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[Initialize](#initialize)|プロバイダーが開始されます。|
|[初期化を解除します。](#uninitialize)|プロバイダーを停止します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_dwStatus](#dwstatus)|データ ソースのフラグ。|
|[m_pCUtlPropInfo](#pcutlpropinfo)|DB のプロパティ情報の実装へのポインター。|

## <a name="remarks"></a>Remarks

データ ソース オブジェクトと列挙子の省略可能なインターフェイスの必須のインターフェイスです。

## <a name="idbinitializeimpl"></a> IDBInitializeImpl::IDBInitializeImpl

コンストラクターです。

### <a name="syntax"></a>構文

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Remarks

すべてのデータ メンバーを初期化します。

## <a name="initialize"></a> IDBInitializeImpl::Initialize

そのプロパティのサポートを準備して、データ ソース オブジェクトを初期化します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Remarks

参照してください[idbinitialize::initialize](/previous-versions/windows/desktop/ms718026(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize

データの場所はソース プロパティのサポートなどの内部リソースを解放して初期化されていない状態でのオブジェクトです。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Remarks

参照してください[:uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus

データ ソースのフラグ。

### <a name="syntax"></a>構文

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Remarks

これらのフラグは、データ ソース オブジェクトのさまざまな属性の状態を示すまたは指定します。 次の 1 つ以上含む**enum**値。

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|初期化されていない状態の復元を有効にするマスク。|
|`DSF_PERSIST_DIRTY`|(変更されている) 場合は、データ ソース オブジェクトに永続化が必要な場合に設定します。|
|`DSF_INITIALIZED`|データ ソースが初期化されている場合に設定します。|

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo

DB のプロパティ情報の実装オブジェクトへのポインター。

### <a name="syntax"></a>構文

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)