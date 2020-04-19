---
title: 'チュートリアル: プロジェクトのテスト (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: e0422b4f862b5438a313e25dac421d591bbbb9a5
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273699"
---
# <a name="walkthrough-testing-a-project-c"></a>チュートリアル: プロジェクトのテスト (C++)

デバッグ モードでプログラムを実行すると、ブレークポイントを使用してプログラムを停止し、変数およびオブジェクトの状態を調べることができます。

このチュートリアルでは、プログラムの実行による変数の値の変化を観察し、予測どおりの値にならない理由を推測します。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルは、C++ 言語の基本を理解していることを前提としています。

- また、これまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了していることも必要です。

### <a name="to-run-a-program-in-debug-mode"></a>プログラムをデバッグ モードで実行するには

1. 編集する Games.cpp を開きます。

1. 次のコード行を選択します。

   `Cardgame solitaire(1);`

1. その行にブレークポイントを設定するには、メニュー バーで **[デバッグ]**  >  **[ブレークポイントの設定/解除]** の順に選択するか、**F9** キーを押します。 赤い円が行の左側に表示されて、その行にブレークポイントが設定されていることを示します。 ブレークポイントを削除するには、もう一度メニュー コマンドを選択するか **F9** キーを押します。

   マウスを使用している場合は、左の余白をクリックすることでブレークポイントを設定/解除できます。

1. メニュー バーで **[デバッグ]**  >  **[デバッグ開始]** の順に選択するか、**F5** キーを押します。

   プログラムがブレークポイントの行に到達すると、実行が一時的に停止されます。プログラムが中断モードであるためです。 コード行の左側の黄色の矢印は、次に実行される行を示します。

1. `Cardgame::totalParticipants` 変数の値を調べるには、ポインターを `Cardgame` に移動し、ヒント ウィンドウの左側にある展開コントロールに移動します。 変数の名前 "`totalParticipants`" とその値 "**12**" が表示されます。

   `Cardgame::totalParticipants` 変数のショートカット メニューを開き、 **[ウォッチ式の追加]** を選択して、その変数を **[ウォッチ 1]** ウィンドウに表示します。 変数を強調表示して **[ウォッチ 1]** ウィンドウにドラッグしてもかまいません。

1. コードの次の行に進むために、メニュー バーで **[デバッグ]**  >  **[ステップ オーバー]** の順に選択するか、**F10** キーを押します。

   **[ウォッチ 1]** ウィンドウに、`Cardgame::totalParticipants` の値が "**13**" と表示されます。

1. `return 0;` ステートメントのショートカット メニューを開き、 **[カーソル行の前まで実行]** を選択します。 コード左側の黄色の矢印は、次に実行されるステートメントを示します。

1. `Cardgame::totalParticipants` の値は `Cardgame` が終了すると減ります。 この時点では、すべての `Cardgame` インスタンスが削除されているため `Cardgame::totalParticipants` は 0 のはずですが、 **[ウォッチ 1]** ウィンドウには `Cardgame::totalparticipants` が "**18**" と表示されています。 この差は、コードにバグがあることを示しています。次の「[チュートリアル: プロジェクトのデバッグ (C++)](../ide/walkthrough-debugging-a-project-cpp.md)」チュートリアルを完了することで、そのバグを検出して修正できます。

1. プログラムを停止するために、メニュー バーで **[デバッグ]**  >  **[デバッグの停止]** の順に選択するか、**Shift** + **F5** キーボード ショートカットを使用します。

## <a name="next-steps"></a>次の手順

**前へ:** [チュートリアル:プロジェクトの構築 (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**次へ:** [チュートリアル:プロジェクトのデバッグ (C++)](../ide/walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
