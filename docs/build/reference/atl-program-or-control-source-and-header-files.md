---
title: ATL プログラムまたはコントロールのソース ファイルとヘッダー ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 5c1e5fc111b38fc9e4173598f11fbad7a658d755
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707507"
---
# <a name="atl-program-or-control-source-and-header-files"></a>ATL プログラムまたはコントロールのソース ファイルとヘッダー ファイル

Visual Studio で ATL プロジェクトを作成する場合、作成するプロジェクト用に選択したオプションに応じて、次のファイルが作成されます。

これらのファイルはすべて、*Projname* ディレクトリ、およびソリューション エクスプローラーのヘッダー ファイル (.h ファイル) フォルダーまたはソース ファイル (.cpp ファイル) フォルダーにあります。

|ファイル名|説明|
|---------------|-----------------|
|<*プロジェクト名*>.h|ATLSample.idl に定義されている項目の C++ インターフェイスの定義および GUID の宣言が含まれた主要なインクルード ファイルです。 これは、コンパイル時に MIDL によって再生成されます。|
|*Projname*.cpp|プログラムの主要なソース ファイルです。 これには、インプロセス サーバーの DLL のエクスポートの実装と、ローカル サーバーの `WinMain` の実装が含まれています。 サービス用に、追加ですべてのサービス管理機能が実装されています。|
|Resource.h|リソース ファイルのヘッダー ファイルです。|
|StdAfx.cpp|StdAfx.h および Atlimpl.cpp ファイルが含まれています。|
|StdAfx.h|ATL ヘッダー ファイルを含みます。|

## <a name="see-also"></a>関連項目

[Visual Studio の C++ プロジェクトに対して作成されるファイルの種類](file-types-created-for-visual-cpp-projects.md)<br>
[MFC プログラムまたはコントロールのソース ファイルとヘッダー ファイル](mfc-program-or-control-source-and-header-files.md)<br>
[CLR プロジェクト](files-created-for-clr-projects.md)
