---
title: リンカ ツール エラー LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 57d0c101358f84816c8d0cf96eb5137833df0b48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298741"
---
# <a name="linker-tools-error-lnk2039"></a>リンカ ツール エラー LNK2039

ref クラスをインポートする\<型 >' another.obj で定義されているは、インポートまたは定義されている、両方が可能にする必要があります

Ref クラス ' <`type`>' が指定された .obj ファイルにインポートされますが、別の .obj ファイルにも定義されています。 この条件には、実行時エラーまたはその他の予期しない動作可能性があります。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 確認するかどうか '`type`' その他の .obj ファイルで定義する必要があり、.winmd ファイルからインポートする必要があるかどうかを確認します。

1. 定義またはインポートのいずれかを削除します。

## <a name="see-also"></a>関連項目

[リンカー ツール エラーと警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[リンカー ツール エラー LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)