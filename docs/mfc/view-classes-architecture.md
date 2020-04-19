---
title: ビュー クラス (アーキテクチャ)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: fda4e968a4761fcf1e2245964bd5dca3f41a82ad
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302986"
---
# <a name="view-classes-architecture"></a>ビュー クラス (アーキテクチャ)

`CView` とその派生クラスは、フレームウィンドウのクライアント領域を表す子ウィンドウです。 ビューには、データが表示され、ドキュメントの入力が受け入れられます。

ビュークラスは、ドキュメントクラスと、ドキュメントテンプレートオブジェクトを使用するフレームウィンドウクラスに関連付けられています。

[CView](../mfc/reference/cview-class.md)<br/>
ドキュメントのデータのアプリケーション固有のビューの基本クラス。 ビューデータを表示し、ユーザーの入力を受け入れてデータを編集または選択します。 `CView`からビュークラスを派生させます。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
スクロール機能を持つビューの基本クラスです。 自動スクロール用に `CScrollView` からビュークラスを派生させます。

## <a name="form-and-record-views"></a>フォームビューとレコードビュー

フォームビューはスクロールビューでもあります。 これらは、ダイアログボックステンプレートに基づいています。

レコードビューはフォームビューから派生します。 ダイアログボックステンプレートに加えて、データベースへの接続もあります。

[CFormView](../mfc/reference/cformview-class.md)<br/>
ダイアログボックステンプレートでレイアウトが定義されているスクロールビュー。 ダイアログボックステンプレートに基づいてユーザーインターフェイスを実装するには、`CFormView` からクラスを派生させます。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
データアクセスオブジェクト (DAO) レコードセットオブジェクトに直接接続されたフォームビューを提供します。 すべてのフォームビューと同様に、`CDaoRecordView` はダイアログボックステンプレートに基づいています。 DAO は Access データベースで使用され、Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
アプリケーション内での Web 参照のコントロールをサポートします。 コントロールは、MFC での動的 HTML をサポートします。

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
フォームビューの MFC OLE DB サポートを提供します。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Open Database Connectivity (ODBC) レコードセットオブジェクトに直接接続されたフォームビューを提供します。 すべてのフォームビューと同様に、`CRecordView` はダイアログボックステンプレートに基づいています。

## <a name="control-views"></a>コントロールビュー

コントロールビューでは、コントロールがビューとして表示されます。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows コントロールに関連付けられているすべてのビューの基本クラス。 以下では、コントロールに基づくビューについて説明します。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Windows 標準編集コントロールを含むビュー (「 [CEdit](../mfc/reference/cedit-class.md)」を参照)。 エディットコントロールは、テキストの編集、検索、置換、およびスクロール機能をサポートします。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Windows リッチエディットコントロールを含むビュー (「 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)」を参照)。 リッチエディットコントロールでは、エディットコントロールの機能に加えて、フォント、色、段落書式、および埋め込み OLE オブジェクトがサポートされています。

[CListView](../mfc/reference/clistview-class.md)<br/>
Windows リストコントロールを含むビュー ( [CListCtrl](../mfc/reference/clistctrl-class.md)を参照)。 リストコントロールは、ファイルエクスプローラーの右ペインと同様の方法で、アイコンと文字列を表示します。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Windows ツリーコントロールを含むビュー (「 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)」を参照)。 ツリーコントロールは、ファイルエクスプローラーの左ペインと同様の方法で、階層内に配置されたアイコンと文字列を表示します。

## <a name="see-also"></a>参照

[クラスの概要](../mfc/class-library-overview.md)
