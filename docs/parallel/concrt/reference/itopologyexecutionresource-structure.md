---
title: ITopologyExecutionResource 構造体
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140064"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 構造体

リソース マネージャーで定義される実行リソースへのインターフェイスです。

## <a name="syntax"></a>構文

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[ITopologyExecutionResource:: GetId](#getid)|この実行リソースのリソースマネージャーの一意の識別子を返します。|
|[ITopologyExecutionResource:: GetNext](#getnext)|列挙の順序で次の実行リソースへのインターフェイスを返します。|

## <a name="remarks"></a>解説

このインターフェイスは、通常、リソースマネージャーによって監視されるシステムのトポロジを調べるために使用されます。

## <a name="inheritance-hierarchy"></a>継承階層

`ITopologyExecutionResource`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="getid"></a>ITopologyExecutionResource:: GetId メソッド

この実行リソースのリソースマネージャーの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

この実行リソースのリソースマネージャーの一意の識別子。

## <a name="getnext"></a>ITopologyExecutionResource:: GetNext メソッド

列挙の順序で次の実行リソースへのインターフェイスを返します。

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>戻り値

列挙順序での次の実行リソースへのインターフェイス。 この実行リソースが属しているノードの列挙順序にノードがそれ以上ない場合、このメソッドは `NULL`値を返します。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
