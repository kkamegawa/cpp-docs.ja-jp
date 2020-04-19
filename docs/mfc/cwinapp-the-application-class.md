---
title: CWinApp:Application クラス
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: d9f0d4f5ba6b6b070b23ce98ecda8c7accf44934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241563"
---
# <a name="cwinapp-the-application-class"></a>CWinApp:Application クラス

Mfc アプリケーションのメイン クラスには、初期化、実行、および Windows オペレーティング システム用のアプリケーションの終了がカプセル化します。 フレームワークで構築されたアプリケーションには、いずれかが必要し、から派生したクラスのオブジェクトを 1 つだけ[CWinApp](../mfc/reference/cwinapp-class.md)します。 Windows が作成される前に、このオブジェクトが構築されます。

`CWinApp` 派生`CWinThread`、1 つまたは複数のスレッドがありますアプリケーションの実行のメイン スレッドを表します。 MFC の最近のバージョンで、 `InitInstance`、**実行**、 `ExitInstance`、および`OnIdle`クラスでメンバー関数が実際には`CWinThread`します。 場合と同様、これらの関数はここで説明`CWinApp`メンバー代わりに、あるプライマリ スレッドではなくアプリケーション オブジェクトとしてのオブジェクトの役割。

> [!NOTE]
>  アプリケーション クラスでは、実行のアプリケーションのプライマリ スレッドを構成します。 Win32 API 関数を使用して、セカンダリ スレッドを作成することもできます。 これらのスレッドは、MFC ライブラリを使用できます。 詳細については、次を参照してください。[マルチ スレッド](../parallel/multithreading-support-for-older-code-visual-cpp.md)します。

Windows オペレーティング システムの任意のプログラムと同様に、framework のアプリケーションがあります、`WinMain`関数。 Framework アプリケーションでは、ただし、書き`WinMain`します。 クラス ライブラリによって提供され、アプリケーションが起動するときに呼び出されます。 `WinMain` ウィンドウ クラスの登録などの標準的なサービスを実行します。 呼び出してメンバーを初期化し、アプリケーションを実行するアプリケーション オブジェクトの関数。 (カスタマイズできる`WinMain`オーバーライドすることで、`CWinApp`メンバー関数を`WinMain`呼び出し)。

アプリケーションを初期化するために`WinMain`アプリケーション オブジェクトの呼び出し`InitApplication`と`InitInstance`メンバー関数。 アプリケーションのメッセージ ループを実行する`WinMain`呼び出し、**実行**メンバー関数。 、終了時に`WinMain`アプリケーション オブジェクトの呼び出し`ExitInstance`メンバー関数。

> [!NOTE]
>  表示される名前**太字**このドキュメントでは、Microsoft Foundation Class ライブラリと Visual C によって指定された要素を示します。 表示される名前`monospaced`型が作成または上書きされた要素を示しています。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)<br/>
[CWinApp および MFC アプリケーション ウィザード](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[オーバーライド可能な CWinApp のメンバー関数](../mfc/overridable-cwinapp-member-functions.md)<br/>
[CWinApp のその他のサービス](../mfc/special-cwinapp-services.md)
