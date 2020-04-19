---
title: IConvertTypeImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: 546a5a007f9e4c1c2a0e581eff2e7984947bdbb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408993"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl クラス

実装を提供、 [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`IConvertTypeImpl`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[CanConvert](#canconvert)|コマンドまたは行セットでは、型変換の可用性に関する情報を示します。|

## <a name="remarks"></a>Remarks

このインターフェイスは、コマンド、行セット、およびインデックスの行セットでは必須です。 `IConvertTypeImpl` OLE DB によって指定されている変換オブジェクトに委任することで、インターフェイスを実装します。

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert

コマンドまたは行セットでは、型変換の可用性に関する情報を示します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>パラメーター

参照してください[IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="remarks"></a>Remarks

OLE DB データ変換を使用して`MSADC.DLL`します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)