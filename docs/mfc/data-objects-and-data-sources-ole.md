---
title: データ オブジェクトとデータ ソース (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 485fa5c62aafa4c116a76547238325d2979bfdc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241211"
---
# <a name="data-objects-and-data-sources-ole"></a>データ オブジェクトとデータ ソース (OLE)

データ転送では、クリップボードまたはドラッグ アンド ドロップを使用して、いずれかを実行すると、データは、ソースとターゲットをが。 1 つのアプリケーションをコピーするためのデータの提供を貼り付けるのための別のアプリケーションを受け取り、引き受けます。 転送のそれぞれの側は、同じデータを正常に転送するためにさまざまな操作を実行する必要があります。 Microsoft Foundation Class (MFC) ライブラリには、この転送のそれぞれの側を表す 2 つのクラスが用意されています。

- データ ソース (によって実装される`COleDataSource`オブジェクト) データ転送のソース側を表します。 データがクリップボードにコピーする場合、またはドラッグ アンド ドロップ操作のデータが提供されている場合、送信元アプリケーションによって作成されます。

- データ オブジェクト (によって実装される`COleDataObject`オブジェクト) データ転送のターゲット側を表します。 コピー先のアプリケーションがあるデータの削除を使用するか、クリップボードから貼り付け操作の実行が要求されたときに作成されます。

次の記事では、データ オブジェクトと、アプリケーションでデータ ソースを使用する方法について説明します。 この情報は、両方をコピーして貼り付けるデータ時に呼び出すことがあるために、コンテナーとサーバーの両方のアプリケーションに適用されます。

- [データ オブジェクトとデータ ソース: 作成と破棄](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [データ オブジェクトとデータ ソース: 操作](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>このセクションの内容

[ドラッグ アンド ドロップ](../mfc/drag-and-drop-ole.md)

[クリップボード](../mfc/clipboard.md)

## <a name="see-also"></a>関連項目

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleDataObject クラス](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource クラス](../mfc/reference/coledatasource-class.md)
