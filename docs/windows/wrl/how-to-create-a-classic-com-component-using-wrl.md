---
title: '方法: WRL を使用した従来の COM コンポーネントを作成します。'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: e19ff4a331a98e64c39dc2e163459b2696bbdee5
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893731"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>方法: WRL を使用した従来の COM コンポーネントを作成します。

Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用して、ユニバーサル Windows プラットフォーム (UWP) アプリを使用することだけでなく、デスクトップ アプリで使用するための基本的な従来の COM コンポーネントを作成することができます。 Windows ランタイム C++ テンプレート ライブラリの COM コンポーネントの作成、ATL よりも少ないコードを必要があります。 Windows ランタイム C++ テンプレート ライブラリをサポートする COM のサブセットの詳細については、次を参照してください。 [Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)します。

このドキュメントでは、Windows ランタイム C++ テンプレート ライブラリを使用して基本的な COM コンポーネントを作成する方法を示します。 ニーズに最適な配置メカニズムを使用できますが、このドキュメントでは、デスクトップ アプリから COM コンポーネントを登録して使用する基本的な方法についても説明します。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Windows ランタイム C++ テンプレート ライブラリを使用して基本的な従来の COM コンポーネントを作成するには

1. Visual Studio で、作成、**空のソリューション**プロジェクト。 など、プロジェクトの名前`WRLClassicCOM`します。

2. 追加、 **Win32 プロジェクト**をソリューションにします。 など、プロジェクトの名前`CalculatorComponent`します。 **アプリケーション設定**] タブで [ **DLL**します。

3. 追加、 **Midl ファイル (.idl)** ファイルをプロジェクトにします。 など、ファイルの名前`CalculatorComponent.idl`します。

4. CalculatorComponent.idl に次のコードを追加します。

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. CalculatorComponent.cpp で、`CalculatorComponent` クラスを定義します。 `CalculatorComponent`クラスから継承[:runtimeclass](runtimeclass-class.md)します。 [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md)クラスの派生元を指定します。 [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)なく[IInspectable](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)します。 (`IInspectable`は Windows ランタイム アプリのコンポーネントでのみ使用できます)。`CoCreatableClass`などの関数で使用できるクラスのファクトリを作成[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)します。

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 次のコードを使用して、コードに置き換えます`dllmain.cpp`します。 このファイルで DLL のエクスポート関数が定義されます。 これらの関数を使用して、 [Microsoft::WRL::Module](module-class.md)モジュールのクラス ファクトリを管理するクラス。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 追加、**モジュール定義ファイル (.def)** ファイルをプロジェクトにします。 など、ファイルの名前`CalculatorComponent.def`します。 このファイルによって、エクスポートされる関数の名前がリンカーに設定されます。

8. CalculatorComponent.def に次のコードを追加します。

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. リンカー行に runtimeobject.lib を追加します。 学習する方法についてを参照してください[します。Lib ファイルをリンカー入力として](../../build/reference/dot-lib-files-as-linker-input.md)します。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>デスクトップ アプリから COM コンポーネントを使用するには

1. Windows レジストリを使用して COM コンポーネントを登録します。 これを行うには、登録エントリ ファイルを作成、名前を付けます`RegScript.reg`、次のテキストを追加します。 置換 *\<dll パス >* 、DLL のパスを使用 — たとえば、 `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`。

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

2. RegScript.reg を実行するかをプロジェクトの追加**ビルド後イベント**します。 詳細については、次を参照してください。[ビルド前のビルド後コマンド ライン ダイアログ ボックス](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)します。

3. 追加、 **Win32 コンソール アプリケーション**プロジェクトがソリューションにします。 など、プロジェクトの名前`Calculator`します。

4. このコードの内容を使用して`Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>信頼性の高いプログラミング

このドキュメントでは、標準の COM 関数を使用して、COM コンポーネントを作成して、任意の COM 対応テクノロジで使用できるようにする Windows ランタイム C++ テンプレート ライブラリを使用できることを示します。 など、Windows ランタイム C++ テンプレート ライブラリの型を使用することもできます。 [Microsoft::WRL::ComPtr](comptr-class.md) COM およびその他のオブジェクトの有効期間を管理、デスクトップ アプリでします。 次のコードの有効期間を管理する Windows ランタイム C++ テンプレート ライブラリを使用して、`ICalculatorComponent`ポインター。 `CoInitializeWrapper` クラスは RAII ラッパーでの 1 つで、COM ライブラリが解放されることと、COM ライブラリの有効期間が `ComPtr` スマート ポインター オブジェクトよりも長く続くことを保証します。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)