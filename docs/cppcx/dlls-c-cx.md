---
title: DLL (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740271"
---
# <a name="dlls-ccx"></a>DLL (C++/CX)

Visual Studio を使用して、ユニバーサル Windows プラットフォーム (UWP) アプリで使用できる標準の Win32 DLL または Windows ランタイムコンポーネント DLL を作成できます。 Visual studio のバージョンまたは Visual Studio 2012 より前の Microsoft C++コンパイラを使用して作成された標準 DLL は、UWP アプリに正しく読み込まれない可能性があり、Microsoft Store のアプリ検証テストに合格しない可能性があります。

## <a name="windows-runtime-component-dlls"></a>Windows ランタイムコンポーネント Dll

ほとんどの場合、UWP アプリで使用するための DLL を作成する場合は、その名前のプロジェクトテンプレートを使用して、その DLL を Windows ランタイムコンポーネントとして作成します。 パブリックまたはプライベート Windows ランタイム型を持つ Dll の Windows ランタイムコンポーネントプロジェクトを作成できます。 Windows ランタイムコンポーネントには、Windows ランタイム互換の言語で記述されたアプリからアクセスできます。 既定では、Windows ランタイムコンポーネントプロジェクトのコンパイラ設定は **/ZW**スイッチを使用します。 .winmd ファイルには、ルート名前空間と同じ名前が必要です。 たとえば、A.B.C.MyClass という名前のクラスは、A.winmd または A.B.winmd または A.B.C.winmd という名前のメタデータ ファイルで定義されている場合のみインスタンス化できます。 DLL の名前が .winmd ファイル名と一致する必要はありません。

詳細については、「 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)」を参照してください。

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>プロジェクトでサードパーティの Windows ランタイムコンポーネントバイナリを参照するには

1. DLL を使用するプロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。 **[共通プロパティ]** ページで、 **[新しい参照の追加]** をクリックします。

1. Windows ランタイムコンポーネントは、DLL ファイルと、メタデータを含む winmd ファイルで構成されます。 通常、これらのファイルは同じフォルダーにあります。 **[参照の追加]** ダイアログ ボックスの左ペインで、 **[参照]** をクリックし、DLL とその .winmd ファイルの場所に移動します。 詳細については、「[拡張機能 sdk](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks)」を参照してください。

## <a name="standard-dlls"></a>標準 DLL

パブリック Windows ランタイム型を使用またはC++生成せず、UWP アプリから使用するコード用の標準 DLL を作成できます。 このバージョンの Visual Studio でコンパイルするために既存の DLL を移行するだけで、コードを Windows ランタイムコンポーネントプロジェクトに変換しない場合は、ダイナミックリンクライブラリ (DLL) プロジェクトの種類を使用します。 次の手順を使用する場合、DLL は .appx パッケージのアプリ実行可能ファイルと一緒に配置されます。

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Visual Studio で、標準 DLL を作成するには

1. メニューバーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順に選択し、 **[ダイナミックリンクライブラリ (DLL)]** テンプレートを選択します。

1. プロジェクトの名前を入力し、 **[OK]** をクリックします。

1. コードを追加します。 必ず、エクスポートする対象の関数 ( `__declspec(dllexport)` など) の `__declspec(dllexport) Add(int I, in j);`を使用してください。

1. を`#include winapifamily.h`追加して、UWP アプリ用の Windows SDK からそのヘッダーファイルをインクルード`WINAPI_FAMILY=WINAPI_PARTITION_APP`し、マクロを設定します。

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>同じソリューションから標準 DLL プロジェクトを参照するには

1. DLL を使用するプロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。 **[共通プロパティ]** ページで、 **[新しい参照の追加]** をクリックします。

1. 左ペインで **[ソリューション]** をクリックし、右ペインの対応するチェック ボックスをオンにします。

1. ソース コード ファイルで、必要に応じて DLL のヘッダー ファイルの `#include` ステートメントを追加します。

### <a name="to-reference-a-standard-dll-binary"></a>標準 DLL バイナリを参照するには

1. DLL ファイル、.lib ファイル、およびヘッダー ファイルをコピーし、既知の場所 (現在のプロジェクト フォルダーなど) に貼り付けます。

1. DLL を使用するプロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。 **[構成プロパティ]** 、 **[リンカー]** の順にクリックし、 **[入力]** ページで、依存関係として .lib ファイルを追加します。

1. ソース コード ファイルで、必要に応じて DLL のヘッダー ファイルの `#include` ステートメントを追加します。

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>UWP アプリの互換性のために既存の Win32 DLL を移行するには

1. DLL (ユニバーサル Windows) 型のプロジェクトを作成し、既存のソースコードを追加します。

1. を`#include winapifamily.h`追加して、UWP アプリ用の Windows SDK からそのヘッダーファイルをインクルード`WINAPI_FAMILY=WINAPI_PARTITION_APP`し、マクロを設定します。

1. ソース コード ファイルで、必要に応じて DLL のヘッダー ファイルの `#include` ステートメントを追加します。
