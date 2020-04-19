---
title: ITopologyNode 構造体
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140055"
---
# <a name="itopologynode-structure"></a>ITopologyNode 構造体

リソース マネージャーで定義されるトポロジ ノードへのインターフェイスです。 ノードには 1 つ以上の実行リソースが含まれます。

## <a name="syntax"></a>構文

```cpp
struct ITopologyNode;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[ITopologyNode:: GetExecutionResourceCount](#getexecutionresourcecount)|このノードの下にグループ化された実行リソースの数を返します。|
|[ITopologyNode:: GetFirstExecutionResource](#getfirstexecutionresource)|列挙の順序で、このノードの下にグループ化された最初の実行リソースを返します。|
|[ITopologyNode:: GetId](#getid)|このノードのリソースマネージャーの一意の識別子を返します。|
|[ITopologyNode:: GetNext](#getnext)|列挙の順序で次のトポロジノードへのインターフェイスを返します。|
|[ITopologyNode:: GetNumaNode](#getnumanode)|Windows が割り当てた、このリソース マネージャー ノードが属する、NUMA ノードの数を返します。|

## <a name="remarks"></a>コメント

このインターフェイスは、通常、リソースマネージャーによって監視されるシステムのトポロジを調べるために使用されます。

## <a name="inheritance-hierarchy"></a>継承階層

`ITopologyNode`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="getexecutionresourcecount"></a>ITopologyNode:: GetExecutionResourceCount メソッド

このノードの下にグループ化された実行リソースの数を返します。

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>戻り値

このノードの下にグループ化された実行リソースの数。

## <a name="getfirstexecutionresource"></a>ITopologyNode:: GetFirstExecutionResource メソッド

列挙の順序で、このノードの下にグループ化された最初の実行リソースを返します。

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>戻り値

列挙の順序で、このノードの下にグループ化された最初の実行リソース。

## <a name="getid"></a>ITopologyNode:: GetId メソッド

このノードのリソースマネージャーの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

このノードのリソースマネージャーの一意の識別子。

### <a name="remarks"></a>コメント

同時実行ランタイムは、システム上のハードウェアスレッドをプロセッサノードのグループ単位で表します。 通常、ノードはシステムのハードウェアトポロジから派生します。 たとえば、特定のソケットまたは特定の NUMA ノードのすべてのプロセッサが、同じプロセッサノードに属している場合があります。 リソースマネージャーでは、これらのノードに一意の識別子が割り当てられます。これらのノードの `0` は `nodeCount - 1`を含みます。 `nodeCount` は、システム上のプロセッサノードの合計数を表します。

ノードの数は、関数[GetProcessorNodeCount](concurrency-namespace-functions.md)から取得できます。

## <a name="getnext"></a>ITopologyNode:: GetNext メソッド

列挙の順序で次のトポロジノードへのインターフェイスを返します。

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>戻り値

列挙順序での次のノードへのインターフェイス。 システムトポロジの列挙順序にノードがそれ以上ない場合、このメソッドは `NULL`値を返します。

## <a name="getnumanode"></a>ITopologyNode:: GetNumaNode メソッド

Windows が割り当てた、このリソース マネージャー ノードが属する、NUMA ノードの数を返します。

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>戻り値

Windows が割り当てた、このリソース マネージャー ノードが属する、NUMA ノードの数。

### <a name="remarks"></a>コメント

このノードに属する仮想プロセッサ ルートで実行中のスレッド プロキシは、このメソッドが返す NUMA ノードに、少なくとも NUMA ノードのレベルで関係があります。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
