---
title: ウィンドウ クラスの登録
ms.date: 11/04/2016
f1_keywords:
- WndProc
helpviewer_keywords:
- window classes [MFC], registering
- registry [MFC], registering classes
- AfxRegisterWndClass method [MFC]
- MFC, windows
- WinMain method [MFC], and registering window classes
- WndProc method [MFC]
- classes [MFC], registering window classes
- WinMain method [MFC]
- registering window classes [MFC]
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
ms.openlocfilehash: 7c459b909a60fff2b7aeded9ea8d79a39ced24e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309084"
---
# <a name="registering-window-classes"></a>ウィンドウ クラスの登録

Windows の従来のプログラミングでは"ウィンドウ"クラスは、windows の任意の数を作成できますから「クラス」(C++ クラスではなく) の特性を定義します。 この種類のクラスは、テンプレートまたは windows を作成するためのモデルです。

## <a name="window-class-registration-in-traditional-programs-for-windows"></a>Windows 用の従来のプログラムでウィンドウ クラスの登録

MFC では、なし、Windows の従来のプログラムでの「ウィンドウ プロシージャ」でのウィンドウにすべてのメッセージを処理するか、"`WndProc`"。A `WndProc` 「ウィンドウ クラスの登録」プロセスを使用して、ウィンドウに関連付けられています。 メイン ウィンドウに登録されている、`WinMain`関数が windows の他のクラスは、アプリケーションのどこにも登録できます。 登録へのポインターを格納する構造体には、`WndProc`カーソル、背景のブラシの仕様と機能などです。 呼び出す前に、クラスの文字列名と共に、パラメーターとして渡される構造体、`RegisterClass`関数。 したがって、登録クラスは、複数のウィンドウで共有できます。

## <a name="window-class-registration-in-mfc-programs"></a>MFC プログラムでウィンドウ クラスの登録

これに対し、ほとんどのウィンドウ クラスの登録アクティビティは、MFC フレームワーク プログラムで自動的に行われます。 MFC を使用している場合は、通常クラス継承の標準の C++ 構文を使用して、既存のライブラリのクラスから C++ ウィンドウ クラスを派生します。 フレームワークは引き続き従来使用「登録クラス」とは、必要なときに登録されているいくつかの標準的なものを提供します。 追加登録クラスを登録するには、呼び出すことによって、 [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)に登録されているクラスを渡す、グローバル関数、`Create`のメンバー関数`CWnd`します。 ここでは、従来の説明に従って Windows の「登録クラス」は、C++ のクラスと混同しないようにします。

詳細については、次を参照してください。[テクニカル ノート 1:](../mfc/tn001-window-class-registration.md)します。

## <a name="see-also"></a>関連項目

[ウィンドウの作成](../mfc/creating-windows.md)
