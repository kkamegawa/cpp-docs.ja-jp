---
title: ネイティブと .NET の相互運用性
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++]
- .NET Framework [C++], interoperability with Visual C++
- interoperability [C++], about .NET interoperability
- interop [C++], about .NET interoperability
- managed code [C++], interoperability
- native code [C++]
- interoperability [C++]
- MFC [C++], .NET integration
- unmanaged code interoperability [C++]
- Visual C++, interoperability
- native code [C++], .NET interoperatibility
ms.assetid: f3ec6c99-c745-4256-b95b-f1d12ba17a5a
ms.openlocfilehash: 486796e404ad1aee39fbeb85251d26cc078b1160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384791"
---
# <a name="native-and-net-interoperability"></a>ネイティブと .NET の相互運用性

Visual C++ では相互運用機能をサポートしており、マネージド構造とアンマネージド構造が共存して同じアセンブリ内ではもちろん、同じファイル内でも相互運用できます。 この機能の小さなサブセット (P/Invoke など) は他の .NET 言語でもサポートされていますが、Visual C++ が提供する相互運用性サポートのほとんどは他の言語では使用できません。

## <a name="in-this-section"></a>このセクションの内容

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
使用して生成されたアセンブリについて説明します、 [/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)両方を含むコンパイラ オプションがマネージし、アンマネージ機能。

[MFC での Windows フォーム ユーザー コントロールの使用](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
MFC Windows フォーム サポート クラスを使用して MFC アプリケーション内で Windows フォーム コントロールをホストする方法について説明します。

[マネージド コードからのネイティブ関数の呼び出し](../dotnet/calling-native-functions-from-managed-code.md)<br/>
非 CLR DLL を .NET アプリケーションから使用する方法について説明します。
