---
title: オブジェクトの動的生成
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 3478e5481c177e0ebca1e6b5c2cd07509371c5ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173360"
---
# <a name="dynamic-object-creation"></a>オブジェクトの動的生成

この記事では、実行時に動的にオブジェクトを作成する方法について説明します。 プロシージャ、情報の記事で説明したようにランタイム クラス情報を使用して[クラス情報にアクセスする](../mfc/accessing-run-time-class-information.md)します。

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>ランタイム クラスを指定したオブジェクトを動的に作成するには

1. 使用してオブジェクトを動的に作成する次のコードを使用して、`CreateObject`の関数、`CRuntimeClass`します。 失敗した場合、なお`CreateObject`返します**NULL**例外を発生させる代わりに。

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>関連項目

[CObject の使い方](../mfc/using-cobject.md)
