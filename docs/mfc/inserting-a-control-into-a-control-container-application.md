---
title: ActiveX コントロール コンテナー:コントロール コンテナー アプリケーションへのコントロールの追加
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 5f2b964d337ee882bff8acd904ad2fcf64879f88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338234"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX コントロール コンテナー:コントロール コンテナー アプリケーションへのコントロールの追加

ActiveX コントロールは、ActiveX コントロール コンテナー アプリケーションからアクセスできる、前に、コンテナー アプリケーションを使用する ActiveX コントロールを追加する必要があります、 [ActiveX コントロールの挿入](../windows/insert-activex-control-dialog-box.md) ダイアログ ボックス。

ActiveX コントロール コンテナーのプロジェクトには、ActiveX コントロールを追加するを参照してください。[表示およびダイアログ ボックスに ActiveX コントロールを追加](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)します。

コントロールを追加すると、ダイアログ ボックス クラスに (ActiveX コントロールの種類) のメンバー変数を追加する必要があります。 この手順の詳細については、次を参照してください。[メンバー変数の追加](../ide/adding-a-member-variable-visual-cpp.md)します。

追加すると、ラッパー クラスと呼ばれるメンバー変数、クラスが自動的に生成され、プロジェクトに追加します。 このクラスは、コントロール コンテナーと埋め込まれたコントロール間のインターフェイスとして使用されます。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
