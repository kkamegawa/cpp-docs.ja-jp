---
title: WRL 統合 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: a3c8b824d2cd932a7d284804f3f28781654045e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304151"
---
# <a name="wrl-integration-ccx"></a>WRL 統合 (C++/CX)

自由に WRL コードと Windows ランタイム C++ テンプレート ライブラリ (WRL) のコードを混在できます。 同じ翻訳単位で、WRL からオブジェクトへのハンドルで宣言されたオブジェクトを使用することができます (`^`) 表記と WRL のスマート ポインター (`ComPtr<T>`) 表記法。 ただし、戻り値、および WRL HRESULT エラー コードおよび WRL の例外を手動で処理する必要があります。

## <a name="wrl-development"></a>WRL の開発

作成と WRL コンポーネントを利用する方法の詳細についてを参照してください。 [Windows ランタイム C++ テンプレート ライブラリ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)します。

### <a name="example"></a>例

次のコード スニペットでは、WRL および WRL を使用して、Windows ランタイム クラスを使用し、メタデータ ファイルを確認するを示します。

この例は、建物の Microsoft Store アプリのフォーラムでのコード スニペットから取得されます。 このコード スニペットの作成者は、次の免責条項と条件を提示しています。

1. C++ Windows ランタイムの型に反映させる特定の Api を提供しませんが、型の Windows メタデータ ファイル (.winmd) は CLR メタデータ ファイルに完全に準拠します。 Windows は、指定された型の .winmd ファイルを取得するために新しいメタデータ検出 API (RoGetMetaDataFile) を提供しています。 ただし、クラスをインスタンス化できないため、これらの API は C++ 開発者にはあまり役に立ちません。

1. コードをコンパイルした後、Runtimeobject.lib と Rometadata.lib をリンカーに渡す必要もあります。

1. このスニペットは現状のままで示されています。 正しく動作すると予測されますが、エラーが含まれている可能性もあります。

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}
```

## <a name="see-also"></a>関連項目

[その他の言語との相互運用](interoperating-with-other-languages-c-cx.md)
