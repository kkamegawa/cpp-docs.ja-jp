---
title: プリプロセッサ ディレクティブ
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: 86432ebf210523dd958f3258075d9e9c6d3bb4e6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222272"
---
# <a name="preprocessor-directives"></a>プリプロセッサ ディレクティブ

`#define` や`#ifdef`などのプリプロセッサディレクティブは、通常、ソースプログラムの変更を容易にし、異なる実行環境で簡単にコンパイルできるようにするために使用されます。 ソースファイル内のディレクティブは、特定のアクションを実行するようにプリプロセッサに指示します。 たとえば、プリプロセッサは、テキストのトークンを置き換えたり、ソース ファイルに他のファイルの内容を挿入したり、テキストのセクションの削除によりファイルの一部のコンパイルを中止したりできます。 プリプロセッサ行は、マクロの展開の前に認識され、実行されます。 したがって、マクロがプリプロセッサコマンドのようなものに展開されると、プリプロセッサによって認識されません。

プリプロセッサステートメントは、ソースファイルステートメントと同じ文字セットを使用しますが、エスケープシーケンスはサポートされていません。 プリプロセッサ ステートメントで使用される文字セットは、実行文字セットと同じです。 プリプロセッサは、負の文字値も認識します。

プリプロセッサは次のディレクティブを認識します。

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

シャープ記号 (`#`) は、ディレクティブを含む行の最初のシャープ空白文字である必要があります。 数字記号とディレクティブの最初の文字の間に空白文字を含めることができます。 一部のディレクティブには、引数または値が含まれます。 ディレクティブ (ディレクティブの一部である引数または値を除く) の後に続くテキストは、前に単一行コメント区切り記号 (`//`) を付けるか、コメント区切り記号 (`/* */`) で囲む必要があります。 プリプロセッサディレクティブを含む行は、行末のマーカーの直前に円記号 (`\`) を付けて続けることができます。

プリプロセッサディレクティブは、ソースファイル内の任意の場所で使用できますが、ソースファイルの残りの部分にのみ適用されます。

## <a name="see-also"></a>関連項目

[プリプロセッサ演算子](../preprocessor/preprocessor-operators.md)\
[定義済みマクロ](../preprocessor/predefined-macros.md)\
[c/c++ プリプロセッサリファレンス](../preprocessor/c-cpp-preprocessor-reference.md)
