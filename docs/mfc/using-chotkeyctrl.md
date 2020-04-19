---
title: CHotKeyCtrl の使い方
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: f52d676f68718cdd4d16cf93bf0d7e3fd6b03822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349855"
---
# <a name="using-chotkeyctrl"></a>CHotKeyCtrl の使い方

クラスによって表される、ホット キー コントロール[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)は、ユーザーが CTRL + SHIFT + Q など、型、キーの組み合わせのテキスト表現を表示するウィンドウです。 このキーのシフト状態を表すフラグのセットおよび仮想キー コードの形式での内部表現も保持されます。 ホット キー コントロールがホット キーを実際には設定しません-これまで、プログラムはします。 (標準の仮想キー コードの一覧は、Winuser.h を参照してください)。

ホット キー コントロールを使用すると、ウィンドウまたはスレッドに関連付けるホット キーのユーザーの入力を取得できます。 ホット キー コントロールは、ホット キーを割り当てるユーザーを要求するときに表示することもなどのダイアログ ボックスでよく使用されます。 ホット キー コントロールのホット キーを記述する値を取得するウィンドウまたはスレッドにホット キーを関連付ける適切な関数を呼び出すと、プログラムの役目です。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ホット キー コントロールの使い方](../mfc/using-a-hot-key-control.md)

- [ホット キーの設定](../mfc/setting-a-hot-key.md)

- [グローバル ホット キー](../mfc/global-hot-keys.md)

- [スレッド固有のホット キー](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>関連項目

[コントロール](../mfc/controls-mfc.md)
