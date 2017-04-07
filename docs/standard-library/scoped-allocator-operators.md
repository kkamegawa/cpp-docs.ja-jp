---
title: "&lt;scoped_allocator&gt; 演算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c8b64ba6276ecfa1078faf3b75a3cf36e9fc5072
ms.lasthandoff: 02/24/2017

---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; 演算子
|||  
|-|-|  
|[operator!=](#operator_neq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 2 つの `scoped_allocator_adaptor` オブジェクトが等しくないかどうかをテストします。  
  
```cpp  
template <class Outer, class... Inner>  
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>パラメーター  
 `left`  
 左側の `scoped_allocator_adaptor` オブジェクト。  
  
 `right`  
 右側の `scoped_allocator_adaptor` オブジェクト。  
  
### <a name="return-value"></a>戻り値  
 `!(left == right)`  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 2 つの `scoped_allocator_adaptor` オブジェクトが等しいかどうかをテストします。  
  
```cpp  
template <class Outer, class... Inner>  
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>パラメーター  
 `left`  
 左側の `scoped_allocator_adaptor` オブジェクト。  
  
 `right`  
 右側の `scoped_allocator_adaptor` オブジェクト。  
  
### <a name="return-value"></a>戻り値  
 `left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`  
  
## <a name="see-also"></a>関連項目  
 [<scoped_allocator>](../standard-library/scoped-allocator.md)

