---
title: レコード ビューのユーザー インターフェイスの更新 (MFC データ アクセス)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: de94b28e713459edfd63aff832caecc7ea49ca33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152645"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>レコード ビューのユーザー インターフェイスの更新 (MFC データ アクセス)

`CRecordView` 移動コマンド用の既定のユーザー インターフェイス更新ハンドラーを提供します。 これらのハンドラーにより、ユーザー インターフェイス オブジェクト (メニュー項目とツール バー ボタン) の有効/無効が自動的に切り替えられます。 アプリケーション ウィザードは、標準のメニューを提供し、選択した場合、**ドッキング可能ツールバー**オプション、コマンドのツール バー ボタンのセット。 `CRecordView` を使用してレコード ビュー クラスを作成する場合は、同じユーザー インターフェイス オブジェクトをアプリケーションに追加することが必要になることがあります。

### <a name="to-create-menu-resources-with-the-menu-editor"></a>エディター メニューを使用してメニュー リソースを作成するには

1. 使用に関する情報を参照し、[メニュー エディター](../windows/menu-editor.md)、4 つのコマンドを独自のメニューを作成します。

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>グラフィックス エディターを使用してツール バー ボタンを作成するには

1. 使用に関する情報を参照し、[ツール バー エディター](../windows/toolbar-editor.md)、編集、レコード移動コマンド用のツール バー ボタンを追加するツール バー リソース。

## <a name="see-also"></a>関連項目

[レコード ビュー内のナビゲーションのサポート](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[レコード ビューの使用](../data/using-a-record-view-mfc-data-access.md)