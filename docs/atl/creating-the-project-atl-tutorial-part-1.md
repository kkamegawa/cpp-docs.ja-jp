---
title: プロジェクトの作成 (ATL チュートリアル、パート 1)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 5bb4c6edffd13e13a451b203feea9a03461a9318
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108381"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>プロジェクトの作成 (ATL チュートリアル、パート 1)

このチュートリアルでは、多角形を表示する ActiveX オブジェクトを作成する、属性のない ATL プロジェクトのステップバイステップの手順について説明します。 オブジェクトには、多角形を構成する辺の数をユーザーが変更できるようにするためのオプション、および表示を更新するためのコードが含まれています。

> [!NOTE]
> このチュートリアルでは、Polygon サンプルと同じソースコードを作成します。 ソースコードが手動で入力されないようにする場合は、 [Polygon sample abstract](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon)からダウンロードできます。 その後、チュートリアルで作業するときに Polygon ソースコードを参照するか、またはそれを使用して独自のプロジェクトでエラーをチェックすることができます。
> コンパイルするには、 *.pch* (Visual Studio 2017 以前では*stdafx.h* ) を開き、次のように置き換えます。
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> with
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> コンパイラは、正常に終了`regsvr32`していないことを通知しますが、コントロールの DLL をビルドし、使用できるようにする必要があります。

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>ATL プロジェクトウィザードを使用して最初の ATL プロジェクトを作成するには

1. Visual Studio 2017 以前のバージョンでは、次のようになります。 > 新しい**プロジェクト**をファイルに**追加** > します。 **[ビジュアルC++ ]** タブを開き、 **[MFC/ATL]** を選択します。 **[ATL プロジェクト]** を選択します。

   Visual Studio 2019 の場合:[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択し、検索ボックスに「atl」と入力して、 **[atl プロジェクト]** を選択します。

1. プロジェクト名として「 *Polygon* 」と入力します。

    通常、ソースコードの場所は既定で \ ユーザー\\\<のユーザー名 > に設定され、新しいフォルダーが自動的に作成されます。

1. Visual Studio 2019 で、既定値をそのまま使用し、[ **OK]** をクリックします。 
   Visual Studio 2017 で **[OK]** をクリックして、 **ATL プロジェクト**ウィザードを開きます。 **[アプリケーションの設定]** をクリックして、使用可能なオプションを表示します。 このプロジェクトはコントロールを作成し、コントロールはインプロセスサーバーである必要があるため、**アプリケーションの種類**は DLL として残しておきます。 **[OK]** をクリックします。

Visual Studio では、複数のファイルを生成することでプロジェクトが作成されます。 オブジェクトを展開することで 、 `Polygon`これらのファイルをソリューションエクスプローラーで表示できます。 ファイルは次のとおりです。

::: moniker range="<=vs-2017"

|File|説明|
|----------|-----------------|
|Polygon|`DllMain`、、 `DllGetClassObject` `DllCanUnloadNow`、 、および`DllUnregisterServer`の実装が含まれています。 `DllRegisterServer` には、プロジェクト内の ATL オブジェクトのリストであるオブジェクトマップも含まれています。 最初は空白になります。|
|Polygon .def|このモジュール定義ファイルは、DLL で必要とされるエクスポートに関する情報をリンカーに提供します。|
|Polygon .idl|インターフェイス定義言語ファイル。オブジェクトに固有のインターフェイスを記述します。|
|Polygon .rgs|このレジストリスクリプトには、プログラムの DLL を登録するための情報が含まれています。|
|Polygon|リソースファイル。最初はバージョン情報とプロジェクト名を含む文字列が含まれています。|
|Resource.h|リソース ファイルのヘッダー ファイルです。|
|Polygonps|このモジュール定義ファイルは、アパートメント間の呼び出しをサポートするプロキシおよびスタブコードに必要なエクスポートに関する情報をリンカーに提供します。|
|stdafx.cpp|`#include` *Stdafx.h*にするファイル。|
|stdafx.h|ATL ヘッダーファイルを`#include`プリコンパイルするファイル。|

::: moniker-end

::: moniker range=">=vs-2019"

|File|説明|
|----------|-----------------|
|Polygon|`DllMain`、、 `DllGetClassObject` `DllCanUnloadNow`、 、および`DllUnregisterServer`の実装が含まれています。 `DllRegisterServer` には、プロジェクト内の ATL オブジェクトのリストであるオブジェクトマップも含まれています。 最初は空白になります。|
|Polygon .def|このモジュール定義ファイルは、DLL で必要とされるエクスポートに関する情報をリンカーに提供します。|
|Polygon .idl|インターフェイス定義言語ファイル。オブジェクトに固有のインターフェイスを記述します。|
|Polygon .rgs|このレジストリスクリプトには、プログラムの DLL を登録するための情報が含まれています。|
|Polygon|リソースファイル。最初はバージョン情報とプロジェクト名を含む文字列が含まれています。|
|Resource.h|リソース ファイルのヘッダー ファイルです。|
|Polygonps|このモジュール定義ファイルは、アパートメント間の呼び出しをサポートするプロキシおよびスタブコードに必要なエクスポートに関する情報をリンカーに提供します。|
|pch|*.Pch*になるファイル`#include` 。|
|.pch. h|ATL ヘッダーファイルを`#include`プリコンパイルするファイル。|

::: moniker-end

1. **ソリューション エクスプローラー**で、`Polygon` プロジェクトを右クリックします。

1. ショートカットメニューの **[プロパティ]** をクリックします。

1. **[リンカー]** をクリックします。 **UserRedirection**オプションを **[はい]** に変更します。

1. **[OK]** をクリックします。

次の手順では、プロジェクトにコントロールを追加します。

[手順2に進みます。](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>関連項目

[チュートリアル](../atl/active-template-library-atl-tutorial.md)
