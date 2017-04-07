---
title: '&lt;istream&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e3607735f989b61f373eb689b8fe3b2dee656f7b
ms.lasthandoff: 02/24/2017

---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef
||||  
|-|-|-|  
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|  
|[wistream](#wistream)|  
  
##  <a name="a-nameiostreama--iostream"></a><a name="iostream"></a>  iostream  
 `char` に特殊化された型 `basic_iostream`。  
  
```  
typedef basic_iostream<char, char_traits<char>> iostream;  
```  
  
### <a name="remarks"></a>コメント  
 この型はテンプレート クラス [basic_ifstream](../standard-library/basic-iostream-class.md) の同意語であり、既定の特性を持つ型 `char` の要素に対して特殊化されています。  
  
##  <a name="a-nameistreama--istream"></a><a name="istream"></a>  istream  
 `char` に特殊化された型 `basic_istream`。  
  
```  
typedef basic_istream<char, char_traits<char>> istream;  
```  
  
### <a name="remarks"></a>コメント  
 この型はテンプレート クラス [basic_istream](../standard-library/basic-istream-class.md) の同意語であり、既定の特性を持つ型 `char` の要素に対して特殊化されています。  
  
##  <a name="a-namewiostreama--wiostream"></a><a name="wiostream"></a>  wiostream  
 `wchar_t` に特殊化された型 `basic_iostream`。  
  
```  
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;  
```  
  
### <a name="remarks"></a>コメント  
 この型はテンプレート クラス [basic_iostream](../standard-library/basic-iostream-class.md) の同意語であり、既定の特性を持つ型 `wchar_t` の要素に対して特殊化されています。  
  
##  <a name="a-namewistreama--wistream"></a><a name="wistream"></a>  wistream  
 `wchar_t` に特殊化された型 `basic_istream`。  
  
```  
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;  
```  
  
### <a name="remarks"></a>コメント  
 この型はテンプレート クラス [basic_istream](../standard-library/basic-istream-class.md) の同意語であり、既定の特性を持つ型 `wchar_t` の要素に対して特殊化されています。  
  
## <a name="see-also"></a>関連項目  
 [\<istream>](../standard-library/istream.md)

