---
title: 単純データ型クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: 4e415805301d7d12bd418a3b55509a7732851492
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307419"
---
# <a name="simple-data-type-classes"></a>単純データ型クラス

描画の座標、文字列、および時間に、次のクラスがカプセル化し、C++ 構文の日付については、便利な許可を使用します。 これらのオブジェクトは、クラス ライブラリの Windows クラスのメンバー関数へのパラメーターとして広く使用されます。 `CPoint`、 `CSize`、および`CRect`に対応しています、**ポイント**、**サイズ**、および**RECT**構造、それぞれ、Windows sdkこれらの C 言語構造体を使用する場合は、これらの C++ クラスのオブジェクトを使用できます。 クラスは、そのメンバー関数を使用しての便利なインターフェイスを提供します。 `CStringT` 非常に柔軟な動的な文字列を提供します。 `CTime`、 `COleDateTime`、 `CTimeSpan`、および`COleTimeSpan`日付と時刻の値を表します。 これらのクラスの詳細については、記事を参照してください。[日付と時刻](../atl-mfc-shared/date-and-time.md)します。

始まるクラス"`COle`"OLE によって提供されるデータ型をカプセル化されます。 これらのデータ型は、その他の OLE 機能を使用するかどうかに関係なく、Windows プログラムで使用できます。

[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)<br/>
文字の文字列を保持します。

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
絶対日付と時刻の値を保持します。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE オートメーションの型のラッパー**日付**します。 日付と時刻の値を表します。

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
相対日付と時刻の値を保持します。

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
相対を保持`COleDateTime`値、2 つの違いなど`COleDateTime`値。

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
(X, y) 座標ペアの保持されます。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
距離、相対位置、または値のペアを保持します。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
四角形領域の座標を保持します。

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Windows イメージ リストの機能を提供します。 イメージ リストは、リスト コントロールとツリー コントロールで使用されます。 また、格納や一連の同じサイズのビットマップの保存にも使用できます。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE オートメーションの型のラッパー**バリアント**します。 内のデータ**バリアント**多くの形式で保存することができます。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE オートメーションの型のラッパー**通貨**小数点の前に、15 桁、4 桁の数字の後に、固定小数点の数値型。

> [!NOTE]
>  `CRect`、 `CSize`、および`CPoint`は ATL または MFC のいずれかのアプリケーションで使用できます。 さらに、`CStringT`提供、MFC に依存しない`CString`-などのクラス。 共有ユーティリティ クラスの詳細については、次を参照してください。[共有クラス](../atl-mfc-shared/atl-mfc-shared-classes.md)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
