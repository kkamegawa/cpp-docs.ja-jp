---
title: Variant パラメーター型の定数
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: b15a303f69ce13cf3ba3b6c1c0739acdb8a33c7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309481"
---
# <a name="variant-parameter-type-constants"></a>Variant パラメーター型の定数

このトピックでは、Microsoft Foundation Class ライブラリの OLE コントロール クラスで使用するために設計されたバリアント型パラメーターの型を示す新しい定数を使用します。

クラスの定数の一覧を次には。

##  <a name="_mfc_variant_data_constants"></a> Variant データ定数

- VTS_COLOR 32 ビット整数の RGB 色の値を表すために使用します。

- VTS_FONT A のポインター、 `IFontDisp` OLE フォント オブジェクトのインターフェイス。

- VTS_HANDLE A Windows ハンドルの値です。

- VTS_PICTURE A のポインター、 `IPictureDisp` OLE 画像オブジェクトのインターフェイス。

- VTS_OPTEXCLUSIVE 16 ビットの値がラジオ ボタンなどのコントロールのグループで使用するためのものでは、コントロールを使用します。 この型は、グループ内の 1 つのコントロールが TRUE の値を持つ場合は、FALSE をある他のすべて必要がありますをコンテナーに指示します。

- VTS_TRISTATE 16 ビットに符号付き整数の 3 つの値 (選択、消去、利用不可)、たとえば、チェック ボックスのいずれかのプロパティの使用が。

- VTS_XPOS_HIMETRIC 32 ビット符号なし整数 HIMETRIC 単位 x 軸に沿った位置を表すために使用します。

- VTS_YPOS_HIMETRIC 32 ビット符号なし整数 HIMETRIC 単位 y 軸に沿った位置を表すために使用します。

- VTS_XPOS_PIXELS 32 ビット符号なし整数 (ピクセル単位)、x 軸に沿った位置を表すために使用します。

- VTS_YPOS_PIXELS 32 ビット符号なし整数 (ピクセル単位)、y 軸に沿った位置を表すために使用します。

- VTS_XSIZE_PIXELS 32 ビット符号なし整数 (ピクセル単位) 画面オブジェクトの幅を表すために使用します。

- VTS_YSIZE_PIXELS 32 ビット符号なし整数 (ピクセル単位)、画面のオブジェクトの高さを表すために使用します。

- VTS_XSIZE_HIMETRIC 32 ビット符号なし整数 HIMETRIC 単位画面オブジェクトの幅を表すために使用します。

- VTS_YSIZE_HIMETRIC 32 ビット符号なし整数 HIMETRIC 単位画面オブジェクトの高さを表すために使用します。

    > [!NOTE]
    >  追加のバリアント型定数は、すべてのバリアント型を除く VTS_FONT と VTS_PICTURE、variant データ定数へのポインターを提供する定義されています。 これらの定数の名前は、付けを使用して`constantname`規則。 たとえば、VTS_PCOLOR、VTS_COLOR 定数ポインターです。

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
