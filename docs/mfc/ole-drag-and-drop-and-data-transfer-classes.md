---
title: OLE ドラッグ アンド ドロップおよびデータ転送クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: e30a358da55b29f9519bc1ab8ee5c93ada308d98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186063"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE ドラッグ アンド ドロップおよびデータ転送クラス

これらのクラスは、OLE データ転送で使用されます。 これらは、アプリケーションによってクリップボードの使用方法やドラッグ アンド ドロップの間で転送されるデータを許可します。

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
最初から最後までドラッグ アンド ドロップ操作を制御します。 このクラスは、ドラッグ操作の開始時と終了時に決定します。 カーソルからのフィードバックは、ドラッグ アンド ドロップ操作中にも表示されます。

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
アプリケーションでは、データ転送のデータを提供するときに使用します。 `COleDataSource` オブジェクト指向クリップボード オブジェクトとして表示でした。

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
ドラッグ アンド ドロップ操作の対象を表します。 A`COleDropTarget`オブジェクトは画面上のウィンドウに対応します。 すべてのデータにドロップし、実際のドロップ操作を実装をそのまま使用するかどうかが決定します。

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
受信側として使用される`COleDataSource`します。 `COleDataObject` オブジェクトによって格納されるデータにアクセスできるように、`COleDataSource`オブジェクト。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
