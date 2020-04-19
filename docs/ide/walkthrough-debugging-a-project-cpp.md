---
title: 'チュートリアル: プロジェクトのデバッグ (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: ce792345b045a1e647de6363ca094fb3f3826b73
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400977"
---
# <a name="walkthrough-debugging-a-project-c"></a>チュートリアル: プロジェクトのデバッグ (C++)

このチュートリアルでは、プロジェクトのテスト時に見つかった問題を修正するために、プログラムに変更を加えます。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルは、C++ 言語の基本を理解していることを前提としています。

- また、これまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了していることも必要です。

### <a name="to-fix-a-program-that-has-a-bug"></a>バグがあるプログラムを修正するには

1. `Cardgame` オブジェクトが破棄されるとどうなるかを確認するには、`Cardgame` クラスのデストラクターを見ます。

   メニュー バーで **[表示]**  >  **[クラス ビュー]** の順に選択します。

   **[クラス ビュー]** ウィンドウで、 **[Game]** プロジェクト ツリーを展開し、 **[Cardgame]** クラスを選択して、クラス メンバーとメソッドを表示します。

   **~Cardgame(void)** デストラクターのショートカット メニューを開き、 **[定義へ移動]** を選択します。

1. Cardgame が終了したときに `totalParticipants` を減らすには、`Cardgame::~Cardgame` デストラクターの左右の中かっこの間に次のコードを入力します。

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. 変更後、Cardgame.cpp ファイルは次のコードのようになります。

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

1. ビルドが完了したら、メニュー バーの **[デバッグ]**  >  **[デバッグ開始]** を選択するか、または **F5** キーを選択して、デバッグ モードで実行します。 プログラムは、最初のブレークポイントで停止します。

1. プログラムを実行するには、メニュー バーで **[デバッグ]**  >  **[ステップ オーバー]** の順に選択するか、**F10** キーを押します。

   `Cardgame` コンストラクターが実行されるたびに `totalParticipants` の値が増加します。 `PlayGames` 関数が返されると、`Cardgame` インスタンスがスコープ外に出て削除される (デストラクターが呼び出される) ため、`totalParticipants` が減少します。 `return` ステートメントが実行される直前に、`totalParticipants` は 0 になります。

1. プログラムが終了するまで続行するか、またはメニュー バーの **[デバッグ]**  >  **[実行]** を選択するか **F5** キーを選択して続行します。

## <a name="next-steps"></a>次の手順

**前へ:** [チュートリアル:プロジェクトのテスト (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**次へ:** [チュートリアル:プログラムの配置 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
