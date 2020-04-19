---
title: COleDialog クラス
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 353e2ed312fa7dbb9ef7bdfabc2b174abf8e1e1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375718"
---
# <a name="coledialog-class"></a>COleDialog クラス

OLE のダイアログ ボックスに共通の機能が用意されています。

## <a name="syntax"></a>構文

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|ダイアログ ボックスによって返されたエラー コードを取得します。|

## <a name="remarks"></a>Remarks

Microsoft Foundation Class ライブラリは、いくつかのクラスから派生した`COleDialog`:

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

OLE に固有のダイアログ ボックスの詳細については、記事を参照してください。 [OLE のダイアログ ボックス](../../mfc/dialog-boxes-in-ole.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxodlgs.h

##  <a name="getlasterror"></a>  COleDialog::GetLastError

呼び出す、`GetLastError`メンバー関数は、追加のエラー情報を取得するときに`DoModal`IDABORT を返します。

```
UINT GetLastError() const;
```

### <a name="return-value"></a>戻り値

によって返されるエラー コード`GetLastError`表示される特定のダイアログ ボックスに依存します。

### <a name="remarks"></a>Remarks

参照してください、`DoModal`特定のエラー メッセージについては、派生クラスでメンバー関数。

## <a name="see-also"></a>関連項目

[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
