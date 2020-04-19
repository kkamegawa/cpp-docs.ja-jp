---
title: C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: b7deb68a441d392464dad8763f80bd4d9cdfcb17
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493359"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド

Visual Studio では、[分離アプリケーション](/windows/win32/SbsCs/isolated-applications)と[side-by-side アセンブリ](/windows/win32/SbsCs/about-side-by-side-assemblies-)の概念に基づいて、Windows クライアントアプリケーションの配置モデルがサポートされています。 既定では、visual Studio は、VisualC++ C++ライブラリへの依存関係を記述するために[マニフェスト](/windows/win32/sbscs/manifests)を使用する分離アプリケーションとして、すべてのネイティブ C/アプリケーションをビルドします。

C/C++ プログラムを分離アプリケーションとしてビルドすることには、さまざまな利点があります。 たとえば、分離アプリケーションは、他の C/C++ アプリケーションによって Visual C++ ライブラリがインストールまたはアンインストールされる場合に影響を受けません。 分離アプリケーションで使用される Visual C++ ライブラリは、アプリケーションのローカル フォルダーに、またはネイティブ アセンブリ キャッシュ (WinSxS) へのインストールによって、再配布される場合もあります。ただし、 [発行者構成ファイル](/windows/win32/SbsCs/publisher-configuration)を使用することによって、既に配置されているアプリケーションの Visual C++ ライブラリのサービス提供を簡略化できます。 分離アプリケーションの配置モデルにより、特定のコンピューターで実行されている C/C++ アプリケーションで最新バージョンの Visual C++ ライブラリが使用されるようにすることが簡単になります。一方で、アプリケーションが依存する DLL に対する明示的なバージョン バインディングは、引き続きシステム管理者およびアプリケーション作成者が制御できます。

このセクションでは、C/C++ アプリケーションを分離アプリケーションとしてビルドし、マニフェストを使用して Visual C++ ライブラリにバインドされるようにする方法について説明します。 このセクションの情報は、主にネイティブC++アプリケーションまたはアンマネージアプリケーションに適用されます。 Visual Studio でビルドさC++れたネイティブアプリケーションの配置の詳細については、「 [visual C++ Files](../windows/redistributing-visual-cpp-files.md)の再配布」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[分離アプリケーションおよび side-by-side アセンブリの概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[C/C++ 分離アプリケーションのビルド](building-c-cpp-isolated-applications.md)

[C/C++ side-by-side アセンブリのビルド](building-c-cpp-side-by-side-assemblies.md)

[方法: 登録を必要としない COM コンポーネントをビルドする](how-to-build-registration-free-com-components.md)

[方法: COM コンポーネントを使用する分離アプリケーションをビルドする](how-to-build-isolated-applications-to-consume-com-components.md)

[C/C++ プログラムのマニフェスト生成についての理解](understanding-manifest-generation-for-c-cpp-programs.md)

[C/C++ 分離アプリケーションおよび side-by-side アセンブリのトラブルシューティング](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>関連項目

[分離アプリケーションと side-by-side アセンブリ](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[デスクトップ アプリケーションの配置](../windows/deploying-native-desktop-applications-visual-cpp.md)