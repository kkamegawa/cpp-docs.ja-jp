---
title: コレクションと列挙子インターフェイス (ATL) の設計
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: f40c86d3bc8d9b4e4c752fe6657f6a5a14f19e0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234832"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>コレクションと列挙子インターフェイスの設計原則

インターフェイスの種類ごとの背後にあるさまざまな設計原則があります。

- コレクション インターフェイスを提供します*ランダム*へのアクセス、*単一*を使用してコレクション内の項目、`Item`メソッドでは、クライアントを使用してコレクション内の項目の数を検出できます、 `Count`プロパティ、および多くの場合、クライアントが追加および削除できるようにします。

- 列挙子インターフェイス*シリアル*へのアクセスを*複数*コレクション内の項目を検出 (列挙子が返すことを停止するまでに、コレクション内に項目の数は、クライアントを許可しません。アイテム)、および追加の項目を削除する方法を提供しません。

インターフェイスの種類ごとでは、コレクション内の要素へのアクセスを提供するためにさまざまな役割を果たします。

## <a name="see-also"></a>関連項目

[コレクションと列挙子](../atl/atl-collections-and-enumerators.md)
