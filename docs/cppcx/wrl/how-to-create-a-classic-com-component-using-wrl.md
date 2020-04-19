---
title: '方法: WRL を使用して従来の COM コンポーネントを作成する'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: ec762b07caa30ce9aa6f4c67f84bb66ae884a7cf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498389"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>方法: WRL を使用して従来の COM コンポーネントを作成する

Windows ランタイムC++テンプレートライブラリ (wrl) を使用して、ユニバーサル WINDOWS プラットフォーム (UWP) アプリに使用するだけでなく、デスクトップアプリで使用する基本的なクラシック COM コンポーネントを作成することができます。 COM コンポーネントを作成する場合、Windows ランタイムC++テンプレートライブラリでは ATL よりも少ないコードが必要になることがあります。 Windows ランタイムC++テンプレートライブラリでサポートされている COM のサブセットの詳細については、「 [Windows ランタイムC++テンプレートライブラリ (wrl)](windows-runtime-cpp-template-library-wrl.md)」を参照してください。

このドキュメントでは、Windows ランタイムC++テンプレートライブラリを使用して基本的な COM コンポーネントを作成する方法について説明します。 ニーズに最適な配置メカニズムを使用できますが、このドキュメントでは、デスクトップ アプリから COM コンポーネントを登録して使用する基本的な方法についても説明します。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Windows ランタイムC++テンプレートライブラリを使用して基本的なクラシック COM コンポーネントを作成するには

1. Visual Studio で、空の**ソリューション**プロジェクトを作成します。 プロジェクトにという名前を指定`WRLClassicCOM`します。たとえば、のように指定します。

2. ソリューションに**Win32 プロジェクト**を追加します。 プロジェクトにという名前を指定`CalculatorComponent`します。たとえば、のように指定します。 **[アプリケーションの設定]** タブで、 **[DLL]** を選択します。

3. **Midl ファイル (.idl)** ファイルをプロジェクトに追加します。 ファイルにという名前を指定`CalculatorComponent.idl`します。たとえば、のように指定します。

4. CalculatorComponent.idl に次のコードを追加します。

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. CalculatorComponent.cpp で、`CalculatorComponent` クラスを定義します。 クラス`CalculatorComponent`は、 [Microsoft:: wrl:: RuntimeClass](runtimeclass-class.md)から継承されます。 [Microsoft:: wrl:: RuntimeClassFlags\<classiccom >](runtimeclassflags-structure.md)は、クラスが[IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable)ではなく[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)から派生することを指定します。 (`IInspectable`はアプリコンポーネントを Windows ランタイムする場合にのみ使用できます)。[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) などの関数で使用できるクラスのファクトリを作成します。`CoCreatableClass`

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. の`dllmain.cpp`コードを置き換えるには、次のコードを使用します。 このファイルで DLL のエクスポート関数が定義されます。 これらの関数は、 [Microsoft:: WRL:: module](module-class.md)クラスを使用して、モジュールのクラスファクトリを管理します。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. **モジュール定義ファイル (.def)** ファイルをプロジェクトに追加します。 ファイルにという名前を指定`CalculatorComponent.def`します。たとえば、のように指定します。 このファイルによって、エクスポートされる関数の名前がリンカーに設定されます。

8. CalculatorComponent.def に次のコードを追加します。

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. リンカー行に runtimeobject.lib を追加します。 詳細については、「」を参照してください[。リンカー入力としての Lib ファイル](../../build/reference/dot-lib-files-as-linker-input.md)。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>デスクトップ アプリから COM コンポーネントを使用するには

1. Windows レジストリを使用して COM コンポーネントを登録します。 これを行うには、登録エントリファイルを作成し`RegScript.reg`、という名前を入力して、次のテキストを追加します。 *\<Dll パス >* を dll のパスに置き換え`C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`ます (例:)。

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. RegScript .reg を実行するか、プロジェクトの**ビルド後イベント**に追加します。 詳細については、「[ビルド前のイベント/ビルド後のコマンドラインダイアログボックス](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)」を参照してください。

3. **Win32 コンソールアプリケーション**プロジェクトをソリューションに追加します。 プロジェクトにという名前を指定`Calculator`します。たとえば、のように指定します。

4. 次のコードを使用して、 `Calculator.cpp`の内容を置き換えます。

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>信頼性の高いプログラミング

このドキュメントでは、標準の COM 関数を使用して、 C++ Windows ランタイムテンプレートライブラリを使用して com コンポーネントを作成し、任意の com 対応テクノロジで使用できるようにする方法を示します。 また、デスクトップアプリでC++ [Microsoft:: Wrl:: comptr](comptr-class.md)などの Windows ランタイムテンプレートライブラリの種類を使用して、COM とその他のオブジェクトの有効期間を管理することもできます。 次のコードでは、 C++ Windows ランタイムテンプレートライブラリを使用して、 `ICalculatorComponent`ポインターの有効期間を管理します。 `CoInitializeWrapper` クラスは RAII ラッパーでの 1 つで、COM ライブラリが解放されることと、COM ライブラリの有効期間が `ComPtr` スマート ポインター オブジェクトよりも長く続くことを保証します。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)