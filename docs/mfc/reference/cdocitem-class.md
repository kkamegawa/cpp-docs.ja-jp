---
title: CDocItem クラス
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 6c1c1da14d732b6aff6ae07f86ae7b9c1b690b84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168194"
---
# <a name="cdocitem-class"></a>CDocItem クラス

ドキュメント アイテムの基底クラスであり、ドキュメント データのコンポーネントです。

## <a name="syntax"></a>構文

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|項目を含むドキュメントを返します。|
|[CDocItem::IsBlank](#isblank)|アイテムにすべての情報が含まれるかどうかを判断します。|

## <a name="remarks"></a>Remarks

`CDocItem` オブジェクトは、クライアントとサーバーの両方の文書で OLE 項目を表すために使用されます。

詳細については、この記事を参照してください。[コンテナー。コンテナーの実装](../../mfc/containers-implementing-a-container.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole.h

##  <a name="getdocument"></a>  CDocItem::GetDocument

項目を含むドキュメントを取得するには、この関数を呼び出します。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>戻り値

項目を含むドキュメントへのポインターアイテム、ドキュメントの一部でない場合は NULL です。

### <a name="remarks"></a>Remarks

この関数は、派生クラスでオーバーライドされる[COleClientItem](../../mfc/reference/coleclientitem-class.md)と[COleServerItem](../../mfc/reference/coleserveritem-class.md)、いずれかにポインターを返す、 [COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)、または[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)オブジェクト。

##  <a name="isblank"></a>  CDocItem::IsBlank

既定のシリアル化が発生したときに、フレームワークによって呼び出されます。

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>戻り値

アイテムに情報が含まれていない場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

既定では、`CDocItem`オブジェクトは空ではありません。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)オブジェクトから直接派生するためにも空白`CDocItem`します。 ただし、 [COleServerItem](../../mfc/reference/coleserveritem-class.md)オブジェクトが空では常にします。 既定で含まれている OLE アプリケーション`COleClientItem`x または y を持たないオブジェクト エクステントがシリアル化します。 これでのオーバーライドから TRUE が返された`IsBlank`ときに、項目がない x または y エクステント。

シリアル化中に他のアクションを実装する場合は、この関数をオーバーライドします。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDocument クラス](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem クラス](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem クラス](../../mfc/reference/coleclientitem-class.md)
