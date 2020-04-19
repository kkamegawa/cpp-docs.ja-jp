---
title: MFC と ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.topic: overview
ms.openlocfilehash: 87f4a9deb40d7c35498f5cbd66efb6bd976547c2
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274651"
---
# <a name="mfc-and-atl"></a>MFC と ATL

Microsoft Foundation Classes (MFC) は Win32 上の C++ オブジェクト指向ラッパーを提供し、ネイティブ デスクトップ アプリケーションの迅速な開発を可能にします。 Active Template Library (ATL) は COM 開発を簡単にするラッパー ライブラリで、ActiveX コントロールを作成するためによく使用されます。

MFC や ATL プログラムは Visual Studio Community エディションか、それ以上のエディションで作成できます。 Express Edition は、MFC や ATL をサポートしません。

Visual Studio 2015 では、Visual C++ はオプションのコンポーネントです。また、MFC および ATL コンポーネントは Visual C++ のオプションのサブコンポーネントです。 Visual Studio の初回インストール時に、これらのコンポーネントを選択しなかった場合、MFC プロジェクトや ATL プロジェクトを初めて作成したり、開こうとしたときに、これらのコンポーネントをインストールするよう要求されます。

Visual Studio 2017 以降では、MFC と ATL は、Visual Studio インストーラープログラムのワークロード**を使用しC++たデスクトップ開発**の下にあるオプションのサブコンポーネントです。 MFC を使用せずに ATL サポートをインストールすることも、MFC と ATL のサポートを組み合わせることもできます (MFC は ATL に依存します)。 ワークロードとコンポーネントの詳細については、「 [Visual Studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

## <a name="related-articles"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[MFC デスクトップ アプリケーション](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes は Win32 上のオブジェクト指向のシン ラッパーを提供し、C++ の GUI アプリケーションの迅速な開発を可能にします。|
|[ATL COM デスクトップ コンポーネント](../atl/atl-com-desktop-components.md)|ATL は、クラス テンプレートおよびその他の使用のためのコンストラクトを提供し、C++ の COM オブジェクトの作成が簡単にします。|
|[ATL/MFC 共有クラス](../atl-mfc-shared/atl-mfc-shared-classes.md)|MFC および ATL で共有される [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) およびその他のクラスのためのリファレンス。|
|[リソース ファイルの操作](../windows/working-with-resource-files.md)|リソース エディターを使用して、文字列、画像、ダイアログ ボックスなどの UI リソースを編集できます。|
|[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md)|MSDN ライブラリのすべての C++ コンテンツの親トピック。|