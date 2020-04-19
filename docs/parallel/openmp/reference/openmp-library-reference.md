---
title: OpenMP ライブラリ リファレンス
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810742"
---
# <a name="openmp-library-reference"></a>OpenMP ライブラリ リファレンス

OpenMP API で使用される構成要素へのリンクを示します。

OpenMP 標準C++のビジュアル実装には、次の構造体が含まれています。

|構築|説明|
|---------------|-----------------|
|[ディレクティブ](openmp-directives.md)|OpenMP API で使用されるディレクティブへのリンクを提供します。|
|[句](openmp-clauses.md)|OpenMP API で使用される句へのリンクを提供します。|
|[関数](openmp-functions.md)|OpenMP API で使用される関数へのリンクを示します。|
|[環境変数](openmp-environment-variables.md)|OpenMP API で使用される環境変数へのリンクを示します。|

Visual C++ OpenMP ランタイムライブラリ関数は、次のライブラリに含まれています。

|OpenMP ランタイムライブラリ|特性|
|------------------------------|---------------------|
|VCOMP。変数|マルチスレッド、動的リンク (VCOMP140 用のインポートライブラリ)。DLL)。|
|VCOMPD。変数|マルチスレッド、動的リンク (VCOMP140D 用のインポートライブラリ)。DLL) (デバッグ)|

コンパイルで _DEBUG が定義されており、`#include <omp.h>` がソースコード内にある場合は。LIB が既定の lib になります。それ以外の場合は、VCOMP です。LIB が使用されます。

[/NODEFAULTLIB (ライブラリを無視する)](../../../build/reference/nodefaultlib-ignore-libraries.md)を使用して、既定の lib を削除し、選択した lib と明示的にリンクすることができます。

OpenMP Dll は、視覚的C++に再頒布可能なディレクトリにあり、openmp を使用するアプリケーションと共に配布する必要があります。

## <a name="see-also"></a>参照

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
