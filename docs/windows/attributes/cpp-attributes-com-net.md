---
title: COM および .NET 用の C++ の属性
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 4885edf57988d5f83b56ba6a71da85877354d3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491053"
---
# <a name="c-attributes-for-com-and-net"></a>COM および .NET 用の C++ の属性

Microsoft では、COM C++プログラミングを簡略化し、共通言語ランタイム開発を .NET Framework する属性のセットを定義しています。 ソースファイルに属性を含めると、コンパイラはプロバイダー Dll と連携して、生成されたオブジェクトファイルのコードを挿入したりコードを変更したりします。 これらの属性は、.idl ファイル、インターフェイス、タイプライブラリ、およびその他の COM 要素の作成に役立ちます。 統合開発環境 (IDE: integrated development environment) では、属性はウィザードとプロパティウィンドウによってサポートされています。

属性では、COM オブジェクトを記述するために必要な詳細なコーディングの一部が不要ですが、使用するには[com の基礎](/windows/win32/com/the-component-object-model)の背景が必要です。

> [!NOTE]
> C++ 標準属性を探している場合は、「[属性](../../cpp/attributes.md)」を参照してください。

## <a name="purpose-of-attributes"></a>属性の目的

属性はC++ 、現在のところ、言語の従来の構造を壊すことなく、方向に拡張できます。 属性を使用すると、プロバイダー (個別の Dll) は言語機能を動的に拡張できます。 属性の主な目的は、コンポーネント開発者の生産性レベルを高めることに加えて、COM コンポーネントの作成を簡略化することです。 属性は、クラス、データメンバー C++ 、メンバー関数など、ほぼすべてのコンストラクトに適用できます。 この新しいテクノロジによってもたらされる利点を次に示します。

- は、使い慣れた簡単な呼び出し規約を公開します。

- 挿入されたコードを使用します。これはマクロとは異なり、デバッガーによって認識されます。

- は、非常に面倒な実装の詳細がなくても、基本クラスから簡単に派生できます。

- COM コンポーネントに必要な大量の IDL コードを、簡潔な属性で置き換えます。

たとえば、汎用 ATL クラスの単純なイベントシンクを実装するには、 [event_receiver](event-receiver.md)属性をなどの特定のクラス`CMyReceiver`に適用します。 この属性は、Microsoft C++コンパイラによってコンパイルされます。これにより、オブジェクトファイルに適切なコードが挿入されます。 `event_receiver`

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

`CMyReceiver`次に、メソッド`handler1`を設定し`handler2` 、イベントを (組み込み関数[__hook](../../cpp/hook.md)を使用して) イベントソースから処理することができます。これは、 [event_source](event-source.md)を使用して作成できます。

## <a name="basic-mechanics-of-attributes"></a>属性の基本的なしくみ

プロジェクトに属性を挿入するには、次の3つの方法があります。 最初に、ソースコードに手動で挿入することができます。 2つ目は、プロジェクト内のオブジェクトのプロパティグリッドを使用して、それらを挿入する方法です。 最後に、さまざまなウィザードを使用して挿入できます。 **[プロパティ]** ウィンドウおよびさまざまなウィザードの使用方法の詳細については、「 [Visual Studio プロジェクト- C++ ](../../build/creating-and-managing-visual-cpp-projects.md)」を参照してください。

前と同様に、プロジェクトをビルドすると、コンパイラはC++各ソースファイルを解析してオブジェクトファイルを生成します。 ただし、コンパイラが属性を検出すると、解析され、構文的に検証されます。 コンパイラは、コンパイル時にコードを挿入したり他の変更を加えたりするために、属性プロバイダーを動的に呼び出します。 プロバイダーの実装は、属性の型によって異なります。 たとえば、ATL 関連の属性は Atlprov によって実装されます。

次の図は、コンパイラと属性プロバイダーの関係を示しています。

![コンポーネント属性の通信](../media/vccompattrcomm.gif "コンポーネント属性の通信")

> [!NOTE]
> 属性の使用法では、ソースファイルの内容は変更されません。 生成された属性コードが表示されるのは、デバッグセッション中のみです。 さらに、プロジェクト内の各ソースファイルに対して、属性の置換の結果を表示するテキストファイルを生成できます。 この手順の詳細については、「 [/fx (挿入](../../build/reference/fx-merge-injected-code.md)されたコードのマージ)」および「挿入された[コードのデバッグ](/visualstudio/debugger/how-to-debug-injected-code)」を参照してください。

ほとんどC++の構成要素と同様に、属性には適切な使用法を定義する一連の特性があります。 これは、属性のコンテキストと呼ばれ、各属性参照トピックの属性コンテキストテーブルでアドレス指定されます。 たとえば、[コクラス](coclass.md)属性は、 C++ソースファイル内の任意の場所に挿入できる[cpp_quote](cpp-quote.md)属性ではなく、既存のクラスまたは構造体にのみ適用できます。

## <a name="building-an-attributed-program"></a>属性付きプログラムの作成

ソースコードに視覚的C++な属性を設定したら、Microsoft C++コンパイラでタイプライブラリと .idl ファイルを生成することができます。 次のリンカーオプションは、.tlb ファイルと .idl ファイルをビルドするのに役立ちます。

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

一部のプロジェクトには、複数の独立した .idl ファイルが含まれています。 これらは、2つ以上の .tlb ファイルを生成し、必要に応じてリソースブロックにバインドするために使用されます。 このシナリオは、現在、ビジュアルC++ではサポートされていません。

さらに、Visual C++リンカーは、すべての IDL 関連の属性情報を1つの MIDL ファイルに出力します。 1つのプロジェクトから2つのタイプライブラリを生成する方法はありません。

## <a name="contexts"></a>属性コンテキスト

C++属性を記述するには、4つの基本的なフィールドを使用します。これらは、適用先 **(適用先)、** 反復可能かどうか (**反復**可能)、他の属性の必要なもの (**必須属性**)、および非互換性です。他の属性を使用する (**無効な属性**)。 これらのフィールドは、各属性のリファレンストピックの関連するテーブルに一覧表示されます。 これらの各フィールドについて以下に説明します。

### <a name="applies-to"></a>対象

このフィールドは、指定C++された属性の有効なターゲットであるさまざまな言語要素について説明します。 たとえば、属性が **[適用先]** フィールドで "class" を指定している場合、この属性は有効C++なクラスにのみ適用できることを示します。 属性がクラスのメンバー関数に適用されている場合、構文エラーが発生します。

詳細については、「[使用法別の属性](attributes-by-usage.md)」を参照してください。

### <a name="repeatable"></a>反復可能

このフィールドは、属性を同じターゲットに繰り返し適用できるかどうかを示します。 属性の大部分は反復可能ではありません。

### <a name="required-attributes"></a>必要な属性

このフィールドには、指定した属性が正しく機能するために存在する必要がある (つまり、同じターゲットに適用される) 他の属性が一覧表示されます。 属性にこのフィールドのエントリが含まれていることは珍しくありません。

### <a name="invalid-attributes"></a>無効な属性

このフィールドには、指定した属性と互換性のない他の属性が一覧表示されます。 属性にこのフィールドのエントリが含まれていることは珍しくありません。

## <a name="in-this-section"></a>このセクションの内容

[属性プログラミングの FAQ](attribute-programming-faq.md)<br/>
[グループ別の属性](attributes-by-group.md)<br/>
[使用法別の属性](attributes-by-usage.md)<br/>
[属性リファレンス (アルファベット順)](attributes-alphabetical-reference.md)