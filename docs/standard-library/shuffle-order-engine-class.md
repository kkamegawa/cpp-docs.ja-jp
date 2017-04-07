---
title: "shuffle_order_engine クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- shuffle_order_engine
- std::shuffle_order_engine
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- shuffle_order_engine class
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: c4cb4367968c89c42df8580efef06db052c49396
ms.lasthandoff: 02/24/2017

---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine クラス
ベースのエンジンから返された値を並べ替えることで、ランダム シーケンスを生成します。  
  
## <a name="syntax"></a>構文  
  
```  
template <class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Engine`  
 ベースのエンジンの型。  
  
 `K`  
 **テーブル サイズ**。 バッファー (テーブル) 内の要素の数。 **前提条件**: `0 < K`  
  
## <a name="members"></a>メンバー  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 エンジンのメンバーの詳細については、[\<random>](../standard-library/random.md) をご覧ください。  
  
## <a name="remarks"></a>コメント  
 このテンプレート クラスは、ベースのエンジンによって返される値を並べ替えることで値を生成する*エンジン アダプター*を表します。 各コンストラクターは、ベースのエンジンによって返される `K` 個の値を内部テーブルに読み込みます。値が要求されると、テーブルからランダムに要素が選択されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<random>  
  
 **名前空間:** std  
  
## <a name="see-also"></a>関連項目  
 [\<random>](../standard-library/random.md)

