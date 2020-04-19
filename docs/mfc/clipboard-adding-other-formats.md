---
title: クリップボード:その他のデータ形式の追加
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 182abe71ccc9552c113ebb114b4351178e48b096
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151865"
---
# <a name="clipboard-adding-other-formats"></a>クリップボード:その他のデータ形式の追加

このトピックでは、OLE サポートするためのサポートされている形式の一覧を展開する方法について説明します。 トピック[クリップボード。コピーと貼り付けデータ](../mfc/clipboard-copying-and-pasting-data.md)コピーと、クリップボードから貼り付けをサポートするために必要な最低限の実装について説明します。 クリップボードにコピーのみの形式は、すべてを実装する場合は、 **CF_METAFILEPICT**、 **CF_EMBEDSOURCE**、 **CF_OBJECTDESCRIPTOR**、および場合によって**CF_LINKSOURCE**します。 ほとんどのアプリケーションには、これらの 3 つよりも、クリップボードにその他の形式が必要です。

##  <a name="_core_registering_custom_formats"></a> 形式のカスタムの登録

独自のカスタム形式を作成するには、独自のクリップボード形式を登録するときに使用する同じ手順を実行しますする形式の名前を渡す、**独自のデータ**関数および形式 id とその戻り値を使用して。

##  <a name="_core_placing_formats_on_the_clipboard"></a> 形式をクリップボードにコピーします。

オーバーライドする必要がありますにクリップボードに格納されたものをその他の書式を追加する、`OnGetClipboardData`いずれかから派生するクラスの関数`COleClientItem`または`COleServerItem`(データのコピーがネイティブかどうか) によって異なります。 この関数で、次の手順を使用する必要があります。

#### <a name="to-place-formats-on-the-clipboard"></a>クリップボードの形式を配置するには

1. `COleDataSource` オブジェクトを作成します。

1. このデータ ソースを呼び出すことによってサポートされている形式の一覧に、ネイティブ データ形式を追加する関数に渡す`COleDataSource::CacheGlobalData`します。

1. 標準の形式を呼び出すことによって追加`COleDataSource::CacheGlobalData`は、各標準形式をサポートします。

MFC OLE サンプル プログラムでこの手法が使用される[HIERSVR](../overview/visual-cpp-samples.md) (確認、`OnGetClipboardData`のメンバー関数、**よう**クラス)。 このサンプルでは、唯一の違いは、HIERSVR が他の標準形式をサポートしていないため、そのステップ 3 は実装されていません。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [OLE データ オブジェクトとデータ ソースと統一されたデータの転送します。](../mfc/data-objects-and-data-sources-ole.md)

- [OLE ドラッグ アンド ドロップ](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>関連項目

[クリップボード:OLE クリップボード機構の使用方法](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
