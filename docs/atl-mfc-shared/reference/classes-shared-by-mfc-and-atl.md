---
title: MFC と ATL で共有されるクラス
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491455"
---
# <a name="classes-shared-by-mfc-and-atl"></a>MFC と ATL で共有されるクラス

次の表は、MFC と ATL の間で共有されるクラスを示しています。

|クラス|説明|ヘッダー ファイル|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|ファイルに関連付けられた日付と時刻の値を管理するためのメソッドを提供します。|atltime. h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|ファイルに関連付けられている相対的な日付と時刻の値を管理するためのメソッドを提供します。|atltime. h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|固定文字バッファーを持つ文字列オブジェクトを表します。|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|では、JPEG、GIF、BMP、およびポータブルネットワークグラフィックス (PNG) 形式のイメージを読み込んで保存する機能など、ビットマップのサポートが強化されています。|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|OLE オートメーションで使用される日付データ型をカプセル化します。|atlcomtime .h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|時間間隔の相対時間を表します。|atlcomtime .h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|`POINT`構造体を操作`CPoint`するためのメンバー関数も含む、Windows[ポイント](/windows/win32/api/windef/ns-windef-point)構造体に似たクラス。|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|オブジェクトおよび windows `CRect` `RECT`構造体を操作するためのメンバー関数も含む、Windows の[RECT](/windows/win32/api/windef/ns-windef-rect)構造体に似たクラス。|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|オブジェクトを`CSimpleStringT`表します。|atl、pstr .h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|相対座標または位置を実装する Windows の[サイズ](/windows/win32/api/windef/ns-windef-size)構造体に似たクラス。|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|既存`ReleaseBuffer` `GetBuffer` のオブジェクトに対してとを呼び出すための自動リソースクリーンアップを提供します。`CStringT`|atl、pstr .h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|String オブジェクトのデータを表します。|atl、pstr .h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|オブジェクトを`CStringT`表します。|cstringt (MFC 依存) atlstr .h (MFC 非依存)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|絶対時刻と日付を表します。|atltime. h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|期間内の秒数として内部的に格納される時間。|atltime. h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|`CStringT`メモリマネージャーへのインターフェイスを表します。|atl、pstr .h|

## <a name="see-also"></a>関連項目

[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
