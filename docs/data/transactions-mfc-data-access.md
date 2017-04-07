---
title: "トランザクション (MFC データ アクセス) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "データベース [C++], トランザクション"
  - "トランザクション [C++]"
  - "トランザクション [C++], サポート"
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# トランザクション (MFC データ アクセス)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

トランザクションの概念は、データベースの結果の状態が、一連の操作の全体的な成功に依存するケースを処理するために開発されました。  このような状況は、連続した操作によって前の操作の結果が変更される場合があるために発生します。  このような場合は、いずれかの操作が失敗すると、最終的な状態が不定になることがあります。  
  
 この問題を解決するため、トランザクションでは最終的な結果の整合性が確保されるように、一連の操作がグループ化されます。  すべての操作に成功してからコミット \(データベースに書き込み\) するか、トランザクション全体が失敗するかのどちらかとなります。  トランザクションのキャンセルは、ロールバックと呼ばれます。  ロールバックにより、変更を復元し、データベースをトランザクション前の状態に戻すことができます。  
  
 たとえば、自動化された銀行トランザクションで口座 A から口座 B にお金を振り替える場合は、資金を正しく処理するには A からの引き落としと B への預け入れがどちらも成功する必要があります。そうでない場合はトランザクション全体を失敗とします。  
  
 トランザクションは、次の性質を意味する ACID プロパティが必要です。  
  
-   **原子性** トランザクションはアトミックな作業単位であり、1 回のみ実行されます。すべての作業が実行されるか、まったく実行されないかのどちらかです。  
  
-   **一貫性** トランザクションはデータの一貫性を保ち、一貫性のあるデータの状態を別の一貫性のある状態に変換します。  トランザクションにより連結されたデータの意味は保持される必要があります。  
  
-   **分離性** トランザクションは分離単位であり、それぞれが同時トランザクションとは別に独立して発生します。  あるトランザクションが、別のトランザクションの中間段階にかかわらないようにする必要があります。  
  
-   **持続性** トランザクションは復元の単位です。  トランザクションが成功した場合、システムがクラッシュまたはシャットダウンしてもその更新内容は保持されます。  トランザクションが失敗した場合、システムは、そのトランザクションをコミットする前の状態のままになります。  
  
 トランザクションは、OLE DB \(「[OLE DB でのトランザクションのサポート](../data/oledb/supporting-transactions-in-ole-db.md)」を参照\) または ODBC \(「[トランザクション \(ODBC\)](../data/odbc/transaction-odbc.md)」を参照\) でサポートできます。  
  
 分散トランザクションは、分散されたデータ \(複数のネットワーク コンピューター システムにあるデータ\) を更新するトランザクションです。  分散システムでトランザクションをサポートする場合は、OLE DB トランザクション サポートではなく、Microsoft .NET Framework を使用する必要があります。  
  
## 参照  
 [データ アクセス プログラミング \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)