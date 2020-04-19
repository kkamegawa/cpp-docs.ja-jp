---
title: タイプ ライブラリからの MFC クラスの追加
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: e8264de2c717c874da157cb29ad5e336e3ecbd0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296749"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>タイプ ライブラリからの MFC クラスの追加

利用できるタイプ ライブラリ内のインターフェイスからの MFC クラスを作成するのにには、このウィザードを使用します。 MFC クラスは、[MFC アプリケーション](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)、または [MFC ActiveX コントロール](../../mfc/reference/creating-an-mfc-activex-control.md)に追加できます。

> [!NOTE]
>  タイプ ライブラリからクラスを追加する有効な Automation の MFC プロジェクトを作成する必要はありません。

タイプ ライブラリには、パラメーターと戻り値の型とメソッドを定義する、コンポーネントによって公開されるインターフェイスのバイナリ記述が含まれています。 表示するため、タイプ ライブラリを登録する必要があります、**使用可能なタイプ ライブラリ**Typelib ウィザードからのクラスの追加のリスト。 参照してください"内で分散 COM:タイプ ライブラリと言語統合"の詳細については、MSDN ライブラリ。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>タイプ ライブラリからの MFC クラスを追加するには

1. いずれかで**ソリューション エクスプ ローラー**または[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)クラスを追加するプロジェクトの名前を右クリックします。

1. ショートカット メニューの **[追加]**、**[クラスの追加]** を順にクリックします。

1. [クラスの追加](../../ide/add-class-dialog-box.md)ダイアログ ボックスの [テンプレート] ペインで、クリックして**Typelib からの MFC クラス**、順にクリックします**オープン**を表示する、 [Typelib ウィザードからのクラスの追加](../../mfc/reference/add-class-from-typelib-wizard.md).

ウィザードで、タイプ ライブラリでは、複数のクラスを追加できます。 同様に、1 つのウィザード セッションでは、複数のタイプ ライブラリからクラスを追加することができます。

ウィザードから派生した MFC クラスを作成する[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)、選択したタイプ ライブラリから追加する各インターフェイスに対して。 `COleDispatchDriver` OLE オートメーションのクライアント側を実装します。

## <a name="see-also"></a>関連項目

[オートメーション クライアント](../../mfc/automation-clients.md)<br/>
[オートメーション クライアント: タイプ ライブラリの使用](../../mfc/automation-clients-using-type-libraries.md)
