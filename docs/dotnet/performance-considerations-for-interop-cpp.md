---
title: Interop (C++) のパフォーマンスに関する考慮事項
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29dbfa6465f6bcbcf4d0618b1820e59a8edbd3a3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447249"
---
# <a name="performance-considerations-for-interop-c"></a>Interop (C++) のパフォーマンスに関する考慮事項

このトピックでは、実行時のパフォーマンス上の相互運用機能の遷移をマネージ/アンマネージの影響を減らすためのガイドラインを提供します。

Visual C は、Visual Basic および c# (P/invoke) などの他の .NET 言語と相互運用性のと同じメカニズムをサポートしていますが、Visual C (C++ 相互運用機能) に固有の相互運用機能のサポートも提供します。 パフォーマンスが重要なアプリケーションの場合、それぞれの相互運用機能の手法のパフォーマンスに影響を理解しておく必要があります。

使用する相互運用機能手法に関係なく、サンクと呼ばれる特殊な遷移のシーケンスが必要です、マネージ関数は、非管理対象の関数、またはその逆を呼び出すたびに。 このサンクは、Microsoft によって自動的に挿入C++、コンパイラは累積的に、これらの遷移できるパフォーマンスの観点からコストを念頭に重要です。

## <a name="reducing-transitions"></a>遷移の削減

回避またはサンクの相互運用のコストを削減する方法の 1 つでは、マネージ/アンマネージの遷移を最小限に抑えるに関連するインターフェイスをリファクターします。 大幅なパフォーマンス改善を chatty なインターフェイスをマネージ/アンマネージの境界を越えて呼び出し頻度を持たないようなソリューションを対象として指定します。 ループでアンマネージ関数を呼び出すマネージ関数は、たとえば、リファクタリングの適切な候補は。 ループ自体は、アンマネージ側に移動またはアンマネージ呼び出しが作成された場合、管理対象の代わりに (マネージ側のデータをキューにして、ループの後にすべて一度にアンマネージ API にマーシャおそらく) 遷移の数は、符号を削減ificantly します。

## <a name="pinvoke-vs-c-interop"></a>P/invoke vs します。C++ Interop

Visual Basic や c# などの .NET 言語は、ネイティブ コンポーネントとの相互運用の所定の方法は、P/invoke が。 P/invoke は、.NET Framework でサポートされる、ため、Visual C を同様に、そのサポートしますが、Visual C では、C++ Interop と呼ばれる独自の相互運用性サポートも提供します。 C++ Interop は、P/invoke がタイプ セーフではないために、P/invoke 経由で優先します。 その結果、実行時にエラーが報告される主が C++ Interop は P/invoke 経由でパフォーマンス上の利点もあります。

両方の手法では、マネージ関数は、アンマネージ関数を呼び出す際にいくつかの処理が必要です。

- 関数呼び出しの引数は CLR からネイティブ型にマーシャ リングされます。

- マネージとアンマネージ サンクが実行されます。

- (引数のネイティブ バージョンを使用)、アンマネージ関数が呼び出されます。

- アンマネージからマネージへのサンクが実行されます。

- 戻り値の型と"out"または"で, out"引数は、ネイティブ コードから CLR 型にマーシャ リングされます。

マネージ/アンマネージ サンクは、相互運用機能をすべての機能が、関連するデータ型、関数シグネチャ、およびデータの使用方法によって異なりますが、必要なデータのマーシャ リングします。

最も簡単なフォームは、C++ 相互運用機能によって実行されるデータのマーシャ リングしますパラメーターは単にコピー; ビットごとの方法でマネージ/アンマネージ境界を越えて。変換は実行されませんで。 P/invoke では、これはすべてのパラメーターは、簡単な場合は true。 blittable 型です。 それ以外の場合、P/invoke は各管理対象のパラメーターを適切なネイティブ型に変換するには非常に堅牢な手順を実行します。 引数は、"out"としてマークされている場合にその逆の場合、または"で, out"。

つまり、C++ Interop は、P/invoke は、最も堅牢なメソッドを使用して、データのマーシャ リングの最も速い方法を使用します。 つまり、C++ Interop (C++ の標準的な方法) では、既定では、最適なパフォーマンスを提供および、この動作がない場合または安全で適切なアドレス指定するため、プログラマが担当します。

したがって、C++ 相互運用機能には、データのマーシャ リングし、明示的に指定する必要がありますが、利点は、プログラマが、データの性質に応じて、適切な新機能とが使用されるようにする方法を決定することが必要です。 さらに、P/invoke データのマーシャ リングの動作は、ある程度カスタマイズで変更できます、C++ Interop できますデータ マーシャ リングの呼び出しによってごとにカスタマイズします。 これは、P/invoke でことはできません。

C++ 相互運用機能の詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。

## <a name="see-also"></a>関連項目

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
