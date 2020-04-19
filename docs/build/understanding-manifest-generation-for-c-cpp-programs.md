---
title: C/C++ プログラムのマニフェスト生成についての理解
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492522"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>C/C++ プログラムのマニフェスト生成についての理解

[マニフェスト](/windows/win32/sbscs/manifests)は、外部 xml ファイル、またはアプリケーションまたはアセンブリ内に埋め込まれたリソースのいずれかにすることができる xml ドキュメントです。 [分離アプリケーション](/windows/win32/SbsCs/isolated-applications)のマニフェストは、アプリケーションが実行時にバインドする共有 side-by-side アセンブリの名前とバージョンを管理するために使用されます。 Side-by-side アセンブリのマニフェストは、名前、バージョン、リソース、およびその他のアセンブリの依存関係を指定します。

分離アプリケーションまたは side-by-side アセンブリのマニフェストを作成するには、2つの方法があります。 まず、アセンブリの作成者は、規則と名前付けの要件に従ってマニフェストファイルを手動で作成できます。 また、プログラムが CRT、MFC、ATL C++などのビジュアルアセンブリだけに依存している場合は、リンカーによって自動的にマニフェストが生成されるようにすることもできます。

Visual C++ライブラリのヘッダーにはアセンブリ情報が含まれています。また、ライブラリがアプリケーションコードに含まれている場合、このアセンブリ情報はリンカーによって使用され、最終的なバイナリのマニフェストを形成します。 リンカーはマニフェストファイルをバイナリ内に埋め込まず、マニフェストを外部ファイルとしてのみ生成できます。 マニフェストを外部ファイルとして使用すると、すべてのシナリオで機能しない場合があります。 たとえば、プライベートアセンブリには埋め込みマニフェストを含めることをお勧めします。 Nmake を使用したコードのビルドなどのコマンドラインビルドでは、マニフェストツールを使用してマニフェストを埋め込むことができます。詳細について[は、「コマンドラインでのマニフェストの生成](manifest-generation-at-the-command-line.md)」を参照してください。 Visual Studio でビルドする場合、 **[プロジェクトのプロパティ]** ダイアログボックスでマニフェストツールのプロパティを設定することによって、マニフェストを埋め込むことができます。「 [Visual Studio でのマニフェストの生成」を](manifest-generation-in-visual-studio.md)参照してください。

## <a name="see-also"></a>関連項目

[分離アプリケーションおよび side-by-side アセンブリの概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
