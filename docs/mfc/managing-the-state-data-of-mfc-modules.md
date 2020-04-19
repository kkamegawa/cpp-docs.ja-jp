---
title: MFC モジュールの状態データの管理
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: 0cdb368dc70b73ba70b3721fecdaf47de36686d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338370"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>MFC モジュールの状態データの管理

この記事では、MFC のモジュールとの (パスのコードでは、アプリケーションを実行するときに) 実行フロー モジュールに出入りするときにこの状態を更新する方法の状態データについて説明します。 AFX_MANAGE_STATE と METHOD_PROLOGUE マクロでのモジュール状態の切り替えも説明します。

> [!NOTE]
>  「モジュール」とは、実行可能プログラムまたは DLL (または Dll のセット) に、アプリケーションの残りの部分に関係なく動作するが共有 MFC DLL のコピーを使用します。 ActiveX コントロールは、モジュールの典型的な例です。

次の図に示すように、MFC には、アプリケーションで使用される各モジュールの状態データ。 このデータの例としては、Windows のインスタンス ハンドル (リソースの読み込みに使用)、現在へのポインター`CWinApp`と`CWinThread`アプリケーション、OLE モジュールの参照カウントとの間の接続を維持するマップのさまざまなオブジェクトWindows オブジェクトのハンドルと MFC オブジェクトの対応するインスタンス。 ただし、アプリケーションでは、複数のモジュールを使用するときに各モジュールの状態データはアプリケーション全体。 代わりに、各モジュールには、MFC の状態データの独自のコピーがいます。

![1 つのモジュールのデータを状態&#40;アプリケーション&#41;](../mfc/media/vc387n1.gif "状態データを 1 つのモジュールの&#40;アプリケーション&#41;") <br/>
単一モジュール (アプリケーション) の状態データ

モジュールの状態データは、構造体に含まれているしは常にその構造体へのポインターを使用して利用します。 実行のフローでは、次の図に示すように、特定のモジュールが入ると、そのモジュールの状態は「現在」または「効果的な」状態である必要があります。 そのため、各スレッド オブジェクトでは、そのアプリケーションの有効な状態の構造体へのポインターがあります。 このポインターのすべての更新を維持する時間が、アプリケーションのグローバル状態を管理して、各モジュールの状態の整合性を維持に不可欠です。 グローバル状態を正しく管理は、予期しないアプリケーションの動作につながります。

![複数のモジュールのデータを状態](../mfc/media/vc387n2.gif "複数モジュールのデータの状態") <br/>
複数モジュールの状態データ

つまり、各モジュールは、すべてのエントリ ポイントにあるモジュールの状態を正しく切り替えるを担当します。 「エントリ ポイント"は、任意場所の実行フロー モジュール コードを入力できます。 エントリ ポイントは次のとおりです。

- [DLL でエクスポートされた関数](../mfc/exported-dll-function-entry-points.md)

- [COM インターフェイスのメンバー関数](../mfc/com-interface-entry-points.md)

- [ウィンドウ プロシージャ](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
