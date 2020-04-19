---
title: dllexport、dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 2ae284172828ed63b6499475df108c28aecb32ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398928"
---
# <a name="dllexport-dllimport"></a>dllexport、dllimport

**Microsoft 固有の仕様**

**Dllexport**と**dllimport**ストレージ クラス属性は、C および C++ 言語への Microsoft 固有の拡張機能。 それらの属性を使用すると、関数、データ、オブジェクトを DLL との間でエクスポートおよびインポートできます。

## <a name="syntax"></a>構文

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Remarks

これらの属性は、DLL のクライアント (実行可能ファイルまたは別の DLL) に対する DLL のインターフェイスを明示的に定義します。 としての関数の宣言**dllexport**エクスポート関数の仕様は、少なくとも、モジュール定義 (.def) ファイルの必要があります。 **Dllexport**置換の属性、 **_ _export**キーワード。

クラスを declspec(dllexport) とマークした場合、そのクラス階層内のクラス テンプレートの特殊化は暗黙的に declspec(dllexport) とマークされます。 つまり、クラス テンプレートが明示的にインスタンス化され、クラスのメンバーの定義が必要になります。

**dllexport**関数の装飾名を使用して、関数を公開します。 C++ の関数の場合、この処理には名前のマングルが含まれます。 C 関数または `extern "C"` として宣言されている関数の場合、この処理には呼び出し規則に基づいたプラットフォーム固有の装飾が含まれます。 C/C++ コードで名前の装飾については、次を参照してください。[装飾名](../build/reference/decorated-names.md)します。 `__cdecl` 呼び出し規則を使用する エクスポートされた C 関数や C++ `extern "C"` 関数には、名前の装飾が適用されません。

修飾されていない名前をエクスポートするには、EXPORTS セクションに非装飾名を定義したモジュール定義 (.def) ファイルを使用してリンクできます。 詳細については、次を参照してください。[エクスポート](../build/reference/exports.md)します。 非装飾の名前をエクスポートすることもできますが、使用する、`#pragma comment(linker, "/export:alias=decorated_name")`ディレクティブで、ソース コード。

宣言すると**dllexport**または**dllimport**、使用する必要があります[拡張属性構文](../cpp/declspec.md)と **_ _declspec**キーワード。

## <a name="example"></a>例

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

または、コードをより読みやすくするために、マクロ定義を使用できます。

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

詳細については次を参照してください:

- [定義と宣言](../cpp/definitions-and-declarations-cpp.md)

- [dllexport と dllimport を使用したインライン C 関数の定義](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [一般的な規則と制約](../cpp/general-rules-and-limitations.md)

- [C++ クラスでの dllimport と dllexport の使用](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)