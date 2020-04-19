---
title: MFC アプリケーションのローカライズされたリソース:サテライト Dll
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220744"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC アプリケーションのローカライズされたリソース:サテライト Dll

MFC version 7.0 以降では、サテライト Dll の複数の言語にローカライズされるアプリケーションの作成に役立つ機能の強化されたサポートを提供します。 サテライト DLL は、[リソース専用 DLL](creating-a-resource-only-dll.md)特定の言語のローカライズされたアプリケーションのリソースを格納しています。 アプリケーションの実行開始時に MFC には、環境に最も適したローカライズされたリソースが自動的に読み込まれます。 たとえば、2 つのサテライト Dll は、ドイツ語の翻訳を格納している他のリソースのフランス語の翻訳を格納している 1 つの英語リソースをアプリケーションがある可能性があります。 英語の言語がシステム、アプリケーションを実行すると、英語のリソースが使用されます。 フランス語のリソースを使用して、フランス語のシステムで実行される場合ドイツ語のシステムで実行される場合は、ドイツ語のリソースを使用します。

サテライト DLL を読み込むように MFC しよう、MFC アプリケーションでローカライズされたリソースをサポートするためにリソースを含む、特定の言語にローカライズされました。 サテライト Dll の名前は*ApplicationNameXXX*.dll、場所*ApplicationName*の .exe または .dll、MFC を使用して名前を指定し、 *XXX*言語に対する 3 文字コードは、リソース (たとえば、'日本語' または 'DEU')。

MFC では、1 つを見つけたときに停止する順序で、次の言語の各リソース DLL をロードしようとしています。

1. 現在のユーザーの既定の UI 言語、GetUserDefaultUILanguage() Win32 API から返される。

1. サブ言語が指定せず、現在のユーザーの既定の UI 言語 (つまり、ENC [カナダ英語] になる日本語 [米国英語])。

1. システムの既定の UI 言語、GetSystemDefaultUILanguage() API から返されるとします。 その他のプラットフォームでは、これは、OS 自体の言語です。

1. システムの既定の UI 言語、サブ言語が指定なし。

1. 3 文字コード LOC を持つ仮の言語

MFC がサテライト Dll を見つけられない場合は、アプリケーション自体に含まれるすべてのリソースを使用します。

たとえば、LangExample.exe アプリケーションが MFC を使用し、複数のユーザー インターフェイス システム; で実行されているとしますシステム UI 言語が英語 [米国です。英語] 現在のユーザーの UI 言語が FRC [カナダ フランス語] に設定されているとします。 MFC は、次の順序で次の Dll を探します。

1. LangExampleFRC.dll (ユーザーの UI 言語)。

1. LangExampleFRA.dll (フランス語 (フランス) この例では、サブ言語なしのユーザーの UI 言語。

1. LangExampleENU.dll (システムの UI 言語)。

1. LangExampleLOC.dll.

これらの Dll が見つからない場合、MFC は LangExample.exe でリソースを使用します。

## <a name="see-also"></a>関連項目

[Visual Studio で C/C++ Dll を作成します。](dlls-in-visual-cpp.md)<br/>
[テクニカル ノート 57: MFC コンポーネントのローカライズ](../mfc/tn057-localization-of-mfc-components.md)
