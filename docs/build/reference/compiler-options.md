---
title: MSVC コンパイラ オプション
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: ab41a5de027f28b361937e58fb179fd72db54e4e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221746"
---
# <a name="compiler-options"></a>コンパイラ オプション

cl.exe は、Microsoft を制御するツールC++(MSVC) C とC++コンパイラとリンカーします。 cl.exe は、Microsoft Visual Studio for Windows をサポートするオペレーティング システムでのみ実行できます。

> [!NOTE]
> このツールは、Visual Studio 開発者コマンド プロンプトからのみ起動できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。 詳細については、次を参照してください。[コマンドラインから MSVC ツールセットを使用して](../building-on-the-command-line.md)します。

コンパイラは、COFF (Common Object File Format) 形式のオブジェクト (.obj) ファイルを生成します。 リンカーは、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) を生成します。

すべてのコンパイラ オプションで、大文字小文字を区別します。 いずれかにスラッシュを使用することがあります (`/`) またはダッシュ (`-`) コンパイラ オプションを指定します。

リンクなしでコンパイルを使用して、 [/c](c-compile-without-linking.md)オプション。

## <a name="find-a-compiler-option"></a>コンパイラ オプションを見つける

特定のコンパイラ オプションを見つけるには、次のいずれかの一覧を参照してください。

- [アルファベット順のコンパイラ オプション](compiler-options-listed-alphabetically.md)

- [カテゴリ別のコンパイラ オプション](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>コンパイラ オプションを指定します

開発環境での設定方法は、コンパイラの各オプションのトピックで説明します。 開発環境以外からオプションを指定する方法の詳細については、下記を参照してください。

- [MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)

- [CL コマンド ファイル](cl-command-files.md)

- [CL 環境変数](cl-environment-variables.md)

## <a name="related-build-tools"></a>関連するビルド ツール

[MSVC リンカー オプション](linker-options.md)プログラムの構築方法にも影響します。

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)<br/>
[リンカーを呼び出す CL](cl-invokes-the-linker.md)
