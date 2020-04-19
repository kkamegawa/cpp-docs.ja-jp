---
title: C/C++ のプリプロセッサ リファレンス
ms.date: 10/31/2019
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: ef93f2cb98a033eed539ffc25559937b274d8a21
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754085"
---
# <a name="cc-preprocessor-reference"></a>C/C++ のプリプロセッサ リファレンス

『 *C/C++プリプロセッサリファレンス*』では、Microsoft c/C++に実装されているプリプロセッサについて説明しています。 プリプロセッサは C および C++ ファイルをコンパイラに渡す前の準備的な処理を実行します。 プリプロセッサを使用して、コードの条件付きコンパイル、ファイルの挿入、コンパイル時のエラー メッセージの指定、コード セクションへのコンピューター固有の規則の適用を行うことができます。

Visual Studio 2019 では、 [/実験的: プリプロセッサ](../build/reference/experimental-preprocessor.md)コンパイラオプションを使用すると、プリプロセッサの新しい実装が有効になります。 新しい実装はまだ進行中であるため、実験的と見なされます。 最終的には、C99、C11、および C++ 20 に準拠していることを意図しています。 詳細については、「 [MSVC 実験的なプリプロセッサの概要](preprocessor-experimental-overview.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[プリプロセッサ](preprocessor.md)\
従来の試験段階と新しい実験用プリプロセッサの概要について説明します。

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)\
さまざまな実行環境でのソース プログラムの変更やコンパイルを容易にするために通常使用される、ディレクティブについて説明します。

[プリプロセッサ演算子](../preprocessor/preprocessor-operators.md)\
`#define` ディレクティブのコンテキストで使用される、4 つのプリプロセッサ固有の演算子について説明します。

[定義済みマクロ](../preprocessor/predefined-macros.md)\
ANSI および Microsoft C++ 準拠の定義済みマクロについて説明します。

[プラグマ](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
各コンパイラが C 言語および C++ 言語の全体的な互換性を維持しながら、コンピューター固有の機能およびオペレーティング システム固有の機能を提供するために使用される、プラグマについて説明します。

## <a name="related-sections"></a>関連項目

[ C++言語リファレンス](../cpp/cpp-language-reference.md)\
C++ 言語の Microsoft 実装に関するリファレンス ドキュメントを紹介します。

[C 言語リファレンス](../c-language/c-language-reference.md)\
C 言語の Microsoft 実装に関するリファレンス ドキュメントを紹介します。

[C/C++ビルド参照](../build/reference/c-cpp-building-reference.md)\
コンパイラとリンカーのオプション関するトピックへのリンクを示します。

[Visual Studio プロジェクト- C++ ](../build/creating-and-managing-visual-cpp-projects.md)\
プロジェクト システムが C++ プロジェクトのファイルを見つけるために検索するディレクトリを指定できる、Visual Studio のユーザー インターフェイスについて説明します。
