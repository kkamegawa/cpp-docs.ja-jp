---
title: ActiveX コントロールコンテナー:コントロールのプロパティの表示と変更
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 1d42820efd06c2ae52f5d1b22b0bdfb6335c4a89
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907803"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX コントロールコンテナー:コントロールのプロパティの表示と変更

ActiveX コントロールをプロジェクトに挿入する場合は、ActiveX コントロールでサポートされているプロパティを表示および変更すると便利です。 この記事では、ビジュアルC++リソースエディターを使用してこれを行う方法について説明します。

ActiveX コントロールコンテナーアプリケーションで埋め込みコントロールを使用している場合は、リソースエディターでコントロールのプロパティを表示および変更できます。 また、リソースエディターを使用して、デザイン時にプロパティ値を設定することもできます。 リソースエディターは、これらの値をプロジェクトのリソースファイルに自動的に保存します。 その後、コントロールのすべてのインスタンスのプロパティが、これらの値に初期化されます。

この手順では、プロジェクトにコントロールが挿入されていることを前提としています。 詳細について[は、「ActiveX コントロールコンテナー:コントロールコンテナーアプリケーション](../mfc/inserting-a-control-into-a-control-container-application.md)にコントロールを挿入します。

コントロールのプロパティを表示するための最初の手順は、コントロールのインスタンスをプロジェクトのダイアログテンプレートに追加することです。

### <a name="to-view-the-properties-of-a-control"></a>コントロールのプロパティを表示するには

1. リソースビューで、**ダイアログ**フォルダーを開きます。

1. メインダイアログボックステンプレートを開きます。

1. **[Activex コントロールの挿入]** ダイアログボックスを使用して activex コントロールを挿入します。 詳細については、「[ダイアログボックスへの ActiveX コントロールの表示と追加](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)」を参照してください。

1. ダイアログボックスで ActiveX コントロールを選択します。

1. **[プロパティ]** ウィンドウで、 **[プロパティ]** ボタンをクリックします。

**[プロパティ]** ダイアログボックスを使用すると、新しいプロパティをすぐに変更およびテストできます。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
