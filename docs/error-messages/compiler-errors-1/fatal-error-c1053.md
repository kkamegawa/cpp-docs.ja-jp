---
title: "致命的なエラー C1053 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1053"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1053"
ms.assetid: f50c1c6a-d9cc-42fa-984e-4e2e6e9cd1b1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 致命的なエラー C1053
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<identifier\>': 関数が大きすぎます  
  
 コンパイルするには関数が大きすぎます。  
  
### 以下の可能性がある解決策を使って修正するには  
  
1.  最適化せずにコンパイルしてみてください。  
  
2.  大きな関数を小さな関数に分割します。  
  
3.  インライン関数の呼び出しを減らします。