---
title: ボックス化 (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 3f756eaef59c24ca5b82c485bd8352dffe9fb1db
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345767"
---
# <a name="boxing-ccli"></a>ボックス化 (C++/CLI)

ボックス化と値の型を型に変換するプロセスは`object`または値の型によって実装されている任意のインターフェイス型にします。 値をラップするときに、共通言語ランタイム (CLR) は、値の型をボックスに、`System.Object`し、マネージ ヒープに保存します。 ボックス化解除すると、値型がオブジェクトから抽出されます。 ボックス化は暗黙的に行われ、ボックス化解除すると明示的になります。

## <a name="related-articles"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[方法: 明示的にボックス化を要求する](../dotnet/how-to-explicitly-request-boxing.md)|変数に対するボックス化を明示的に要求する方法について説明します。|
|[方法: gcnew を使用して値型を作成し、暗黙的なボックス化を使用する](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|使用する方法を示します`gcnew`に管理され、ガベージ コレクション ヒープ上に配置できる型をボックス化された値を作成します。|
|[方法: ボックス化を解除する](../dotnet/how-to-unbox.md)|ボックス化解除し、値を変更する方法を示します。|
|[標準変換と暗黙のボックス化](../dotnet/standard-conversions-and-implicit-boxing.md)|ボックス化が必要な変換をコンパイラによって、標準変換が選択されていることを示します。|
|[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Visual C のドキュメントでの .NET プログラミングに関する最上位レベルの記事です。|