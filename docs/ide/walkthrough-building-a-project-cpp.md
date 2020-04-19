---
title: 'チュートリアル: プロジェクトの構築 (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: d23412bcc740cbbda4227e0271842b4d44b436af
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400994"
---
# <a name="walkthrough-building-a-project-c"></a>チュートリアル: プロジェクトの構築 (C++)

このチュートリアルでは、コードに意図的に C++ 構文のエラーを挿入し、コンパイル エラーがどのように表示されるかを確認し、その修正方法について説明します。 プロジェクトをコンパイルすると、エラー メッセージによって問題の内容と発生した場所が示されます。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルは、C++ 言語の基本を理解していることを前提としています。

- また、これまでの関連チュートリアル (「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照) を完了していることも必要です。

### <a name="to-fix-compilation-errors"></a>コンパイル エラーを修正するには

1. Game.cpp で、次のステートメントのように最後の行のセミコロンを削除します。

   `return 0`

1. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

1. **[エラー一覧]** ウィンドウに、プロジェクトのビルド中にエラーが発生したことを示すメッセージが表示されます。 たとえば、エラーの説明はこのエラー メッセージのようになります。

   `error C2143: syntax error: missing ';' before '}'`

   このエラーに関するヘルプ情報を表示するには、 **[エラー一覧]** ウィンドウでそのエラーを強調表示し、**F1** キーを押します。

1. 構文エラーのある行の最後に、セミコロンを戻します。

   `return 0;`

1. メニュー バーで、 **[ビルド]**  >  **[ソリューションのビルド]** の順にクリックします。

   **[出力]** ウィンドウに、プロジェクトが正常にコンパイルされたことを示すメッセージが表示されます。

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>次の手順

**前へ:** [チュートリアル:プロジェクトとソリューションの使用 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**次へ:** [チュートリアル:プロジェクトのテスト (C++)](../ide/walkthrough-testing-a-project-cpp.md)

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
