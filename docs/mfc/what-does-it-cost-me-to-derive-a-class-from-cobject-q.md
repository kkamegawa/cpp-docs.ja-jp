---
title: CObject からクラスを派生するときのオーバーヘッド
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: de760a2fd2908595314dc09cf5a317da3581e3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186050"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>CObject からクラスを派生するときのオーバーヘッド

クラスから派生するオーバーヘッド[CObject](../mfc/reference/cobject-class.md)は最小限です。 派生クラスは、4 つだけの仮想関数と、1 つを継承[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)オブジェクト。

## <a name="see-also"></a>関連項目

[CObject クラス: よく寄せられる質問](../mfc/cobject-class-frequently-asked-questions.md)
