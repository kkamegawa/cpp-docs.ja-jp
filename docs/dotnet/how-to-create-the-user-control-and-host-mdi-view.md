---
title: '方法: ユーザー コントロールおよびホスト MDI ビューを作成します。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 7d535fce47be5504f6f521cda1267344206287da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387436"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>方法: ユーザー コントロールおよびホスト MDI ビューを作成します。

次の手順では、.NET Framework ユーザー コントロールを作成し、そのユーザー コントロールをコントロール クラス ライブラリ (特に Windows コントロール ライブラリ プロジェクト) に作成し、プロジェクトをアセンブリにコンパイルする方法について説明します。 コントロールから派生したクラスを使用する MFC アプリケーションから使用できます[CView クラス](../mfc/reference/cview-class.md)と[CWinFormsView クラス](../mfc/reference/cwinformsview-class.md)します。

Windows フォーム ユーザー コントロールを作成およびコントロール クラス ライブラリを作成する方法については、次を参照してください。[方法。ユーザー コントロールを作成](/dotnet/framework/winforms/controls/how-to-author-composite-controls)です。

> [!NOTE]
>  サードパーティのグリッド コントロールなどの Windows フォーム コントロールは、MFC アプリケーションでホストした場合に適切に動作しないことがあります。 この問題の推奨回避策は、Windows フォーム ユーザー コントロールを MFC アプリケーションに配置し、サードパーティのグリッド コントロールをユーザー コントロールの内部に配置することです。

この手順の手順に従って、WindowsFormsControlLibrary1 をという名前の Windows フォーム コントロール ライブラリ プロジェクトを作成することを前提と[方法。ユーザー コントロールおよびホストを作成 ダイアログ ボックスで](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)します。

### <a name="to-create-the-mfc-host-application"></a>MFC ホスト アプリケーションを作成するには

1. MFC アプリケーション プロジェクトを作成します。

   **ファイル**メニューの [**新規**、] をクリックし、**プロジェクト**します。 **Visual C**フォルダーで、 **MFC アプリケーション**します。

   **名前**ボックスに、入力`MFC02`を変更して、**ソリューション**設定**ソリューションに追加**。 **[OK]** をクリックします。

   **MFC アプリケーション ウィザード**すべての既定値をそのまま使用し、クリックして**完了**します。 これにより、マルチ ドキュメント インターフェイスを持つ MFC アプリケーションが作成されます。

1. 共通言語ランタイム (CLR: Common Language Runtime) に対するサポートをプロジェクトに構成します。

   **ソリューション エクスプ ローラー**を右クリックし、`MFC01`プロジェクト ノード、および選択**プロパティ**コンテキスト メニュー。 **プロパティ ページ** ダイアログ ボックスが表示されます。

   **構成プロパティ**を選択します**全般**します。 下、**プロジェクトの既定値**セクションで、設定**共通言語ランタイム サポート**に**共通言語ランタイム サポート (/clr)** します。

   [**構成プロパティ**、展開**C/C++** ] をクリックし、**全般**ノード。 設定**デバッグ情報の形式**に**プログラム データベース (/Zi)** します。

   をクリックして、**コード生成**ノード。 設定**最小リビルドを有効にする**に**いいえ (/Gm-)** します。 設定**基本ランタイム チェック**に**既定**します。

   クリックして**OK**変更を適用します。

1. stdafx.h に、次の行を追加します。

    ```
    #using <System.Windows.Forms.dll>
    ```

1. .NET コントロールへの参照を追加します。

   **ソリューション エクスプ ローラー**を右クリックし、`MFC02`プロジェクト ノードと選択**追加**、**参照**します。 **プロパティ ページ**、 をクリックして**新しい参照の追加**、windowsformscontrollibrary1 (下、**プロジェクト** タブ)、 をクリック**OK**. 形式での参照が追加されます、 [/FU](../build/reference/fu-name-forced-hash-using-file.md)コンパイラ オプションは、プログラムをコンパイルするため; に WindowsFormsControlLibrary1.dll がコピーも、`MFC02`プログラムを実行するためのプロジェクト ディレクトリ。

1. stdafx.h で次の行を見つけます。

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   その上に次の行を追加します。

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 継承するようにビュー クラスを変更[CWinFormsView](../mfc/reference/cwinformsview-class.md)します。

   MFC02View.h、置き換えます[CView](../mfc/reference/cview-class.md)で[CWinFormsView](../mfc/reference/cwinformsview-class.md)コードは次のように表示されるように。

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   呼び出す必要があります、MDI アプリケーションに追加のビューを追加する場合は、[とき](../mfc/reference/cwinapp-class.md#adddoctemplate)のそれぞれのビューを作成します。

1. MFC02View.cpp ファイルを変更して、IMPLEMENT_DYNCREATE マクロとメッセージ マップで CView を CWinFormsView に変更し、既存の空のコンストラクターを次に示すコンストラクターに置き換えます。

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. プロジェクトをビルドして実行します。

   **ソリューション エクスプ ローラー**MFC02 を右クリックし、選択、**スタートアップ プロジェクトとして設定**します。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **デバッグ** メニューのをクリックして**デバッグなしで開始**します。

## <a name="see-also"></a>関連項目

[MFC ビューとしての Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
