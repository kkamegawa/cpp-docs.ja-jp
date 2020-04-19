---
title: C/C++ 分離アプリケーションのビルド
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493345"
---
# <a name="building-cc-isolated-applications"></a>C/C++ 分離アプリケーションのビルド

分離アプリケーションは side-by-side アセンブリにのみ依存し、マニフェストを使用して依存関係にバインドします。 Windows で適切に実行するためにアプリケーションを完全に分離する必要はありません。ただし、アプリケーションの完全な分離に投資することによって、将来アプリケーションをサービスに提供する必要がある場合に時間を節約できます。 アプリケーションを完全に分離する利点の詳細については、「[分離アプリケーション](/windows/win32/SbsCs/isolated-applications)」を参照してください。

Visual Studio を使用してネイティブC++の C/アプリケーションをビルドすると、visual studio プロジェクトシステムによって、visual studio ライブラリに対するアプリケーションの依存関係を記述するマニフェストファイルが生成されます。 アプリケーションが持つ唯一の依存関係である場合、Visual Studio で再構築されるとすぐに、分離されたアプリケーションになります。 アプリケーションが実行時に他のライブラリを使用している場合は、「 [C/C++サイドバイサイドアセンブリのビルド](building-c-cpp-side-by-side-assemblies.md)」で説明されている手順に従って、これらのライブラリを side-by-side アセンブリとして再構築することが必要になる場合があります。

## <a name="see-also"></a>関連項目

[分離アプリケーションおよび side-by-side アセンブリの概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
