---
title: '方法: 既存の MFC リボンをリボン リソースに変換します。'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: b4265a7bf3ebe2c4926f21572d802b75bd525990
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389490"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>方法: 既存の MFC リボンをリボン リソースに変換します。

リボン リソースは、視覚化、変更、および手動でコード化されたリボンより管理しやすくします。 このトピックでは、MFC プロジェクトで手動でコード化されたリボンをリボン リソースに変換する方法について説明します。

たとえば、MFC リボン クラスを使用するコードを含む既存の MFC プロジェクトが必要[CMFCRibbonBar クラス](../mfc/reference/cmfcribbonbar-class.md)します。

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>MFC リボンをリボン リソースに変換するには

1. Visual Studio は、既存の MFC プロジェクトでソース ファイルを開く場所、`CMFCRibbonBar`オブジェクトを初期化します。 通常、ファイルは、mainfrm.cpp です。 リボンの初期化コードの後に、次のコードを追加します。

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   ファイルを保存して閉じます。

1. ビルドし MFC アプリケーションを実行、メモ帳で開き RibbonOutput.txt しその内容をコピーします。

1. Visual Studio での**プロジェクト** メニューのをクリックして**リソースの追加**します。 **リソースの追加**ダイアログ ボックスで、**リボン** をクリックし、**新規**します。

   Visual Studio では、リボン リソースを作成し、デザイン ビューで開かれます。 リボン リソース ID に表示される IDR_RIBBON1**リソース ビュー**します。 リボンは ribbon1.mfcribbon ms XML ファイルで定義されます。

1. Visual Studio で、ribbon1.mfcribbon ms や、その内容を削除しの RibbonOutput.txt で、先ほどコピーした内容を貼り付けます。 保存して ribbon1.mfcribbon ms を閉じます。

1. もう一度 CMFCRibbonBar オブジェクトが初期化されているソース ファイルを開きます (通常、mainfrm.cpp) とリボンのコードを既存のコメント。 コードのコメント アウトした後、次のコードを追加します。

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. プロジェクトをビルドし、プログラムを実行します。

## <a name="see-also"></a>関連項目

[リボン デザイナー (MFC)](../mfc/ribbon-designer-mfc.md)
