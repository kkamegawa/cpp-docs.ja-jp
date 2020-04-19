---
title: /constexpr (constexpr の評価の制御)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 178acc548fb9c89dcfde104d2a12d85637440e28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294253"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (constexpr の評価の制御)

使用して、 **/constexpr**コンパイラのオプションを制御するパラメーターを**constexpr**コンパイル時に評価します。

## <a name="syntax"></a>構文

> **/constexpr:depth**<em>N</em>
>  **/constexpr:backtrace**<em>N</em>
>  **/constexpr:steps**<em>N</em>

## <a name="arguments"></a>引数

**深さ**<em>N</em>再帰の深さを制限する**constexpr**関数の呼び出しに*N*レベル。 既定値は 512 文字です。

**バック トレース**<em>N</em>最大表示*N* **constexpr**診断で評価します。 既定値は 10 です。

**手順**<em>N</em> Terminate **constexpr**後の評価*N*手順を実行します。 既定値には 100,000 です。

## <a name="remarks"></a>Remarks

**/Constexpr**コンパイラ オプションのコンパイル時の評価を制御する**constexpr**式。 評価手順、再帰レベル、およびバック トレースの深さが、コンパイラがあまり時間をかけることを防ぐために管理された**constexpr**評価します。 詳細については、 **constexpr**言語の要素を参照してください[constexpr (C++)](../../cpp/constexpr-cpp.md)します。

**/Constexpr**オプションは、Visual Studio 2015 以降を使用できます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの開く**プロパティ ページ** ダイアログ ボックス。

2. **構成プロパティ**、展開、 **C/C++** フォルダーを選択し、**コマンド ライン**プロパティ ページ。

3. 入力 **/constexpr**コンパイラ オプション、**追加オプション**ボックス。 選択**OK**または**適用**変更を保存します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
