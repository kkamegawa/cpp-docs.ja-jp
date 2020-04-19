---
title: ジェネリック (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- generic_cpp
- generic
helpviewer_keywords:
- generics [C++]
ms.assetid: c7ccc316-a411-4c00-b2e2-f0c0eadc6cfd
ms.openlocfilehash: 31998cf77e3f3cfdc6bc19ad2fc57a50da77e0f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516347"
---
# <a name="generics--ccli-and-ccx"></a>ジェネリック (C++/CLI および C++/CX)

ジェネリックは、パラメーター化された型およびメソッドです。 このセクションでは、Windows ランタイムと共通言語ランタイムの両方でサポートされている汎用的な機能と、共通言語ランタイムのみでサポートされている機能を調べます。 さらに、C++/CLI で独自のジェネリック メソッドと型を作成する方法と、.NET Framework 言語で作成されたジェネリック型を C++/CLI で使用する方法を調べます。 最後に、このセクションでは、ジェネリックと C++ テンプレートを比較します。

## <a name="in-this-section"></a>このセクションの内容

### <a name="supported-by-the-windows-runtime-and-the-common-language-runtime"></a>Windows ランタイムと共通言語ランタイムでサポートされるもの

[C++/CLI でのジェネリックの概要](overview-of-generics-in-visual-cpp.md)<br/>
この言語機能の動機、ジェネリックを記述するために使用される用語の定義、およびジェネリックの型パラメーターとしての参照型と値型の使用に関する情報です。

[ジェネリック インターフェイス (C++/CLI)](generic-interfaces-visual-cpp.md)<br/>
ジェネリック インターフェイスの定義と使用についての情報です。

[汎用デリゲート (C++/CLI)](generic-delegates-visual-cpp.md)<br/>
汎用デリゲートの定義と使用についての情報です。

[ジェネリック型パラメーターの制約 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)<br/>
ジェネリック型での制約の使用についての情報です。

[ジェネリックの使用 (C++/CLI)](consuming-generics-cpp-cli.md)<br/>
.NET アセンブリで定義されたジェネリックを、C++/CLI などの他の言語で使用することについての情報です。

[ジェネリックとテンプレート (C++/CLI)](generics-and-templates-visual-cpp.md)<br/>
ジェネリックとテンプレートを別々に使用した場合の比較と、役立つようにそれらを組み合わせる方法。

### <a name="supported-by-the-common-language-runtime"></a>共通言語ランタイムによってサポートされるもの

[ジェネリック関数 (C++/CLI)](generic-functions-cpp-cli.md)<br/>
ジェネリック関数とメソッドの定義と使用についての情報です。

[ジェネリック クラス (C++/CLI)](generic-classes-cpp-cli.md)<br/>
ジェネリック クラスの定義と使用についての情報です。

## <a name="related-sections"></a>関連項目

[方法: for each を使用してジェネリック コレクションを反復処理する](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)<br/>
ジェネリック コレクションでの [for each, in](../dotnet/for-each-in.md) キーワードの使用

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)