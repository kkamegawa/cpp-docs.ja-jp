---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492883"
---
# <a name="exports"></a>EXPORTS

関数またはデータのエクスポート名または序数を指定する 1 つ以上のエクスポート定義のセクションを導入します。 各定義は個別の行に指定する必要があります。

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Remarks

最初の*定義*は、 `EXPORTS`キーワードと同じ行または後続の行に配置できます。 .DEF ファイルには、1 つ以上の `EXPORTS` ステートメントを含めることができます。

エクスポート*定義*の構文は次のとおりです。

> *entryname*\[ __=__ *internal_name*|*other_module.exported_name*] \[ **\@** _ordinal_ \[**NONAME**] ] \[ \[**PRIVATE**] | \[**DATA**] ]

*entryname*は、エクスポートする関数または変数の名前です。 これは必須です。 エクスポートする名前が DLL 内の名前と異なる場合は、 *internal_name*を使用して、dll 内のエクスポートの名前を指定します。 たとえば、DLL で関数 `func1` をエクスポートし、呼び出し元がそれを `func2` として使用する場合は、次のように指定します。

```DEF
EXPORTS
   func2=func1
```

エクスポートする名前が他のモジュールからのものである場合は、 *other_module. exported_name*を使用して、DLL 内のエクスポートの名前を指定します。 たとえば、DLL で関数 `other_module.func1` をエクスポートし、呼び出し元がそれを `func2` として使用する場合は、次のように指定します。

```DEF
EXPORTS
   func2=other_module.func1
```

エクスポートする名前が、序数でエクスポートされた別のモジュールからのものである場合は、 *other_module*を使用して、DLL 内のエクスポートの序数を指定します。 __#__ *序数*。 たとえば、DLL が序数が42である他のモジュールから関数をエクスポートし、呼び出し元がとして`func2`それを使用するようにする場合は、次のように指定します。

```DEF
EXPORTS
   func2=other_module.#42
```

MSVC コンパイラは関数に名前のC++装飾を使用するため、ソースコードでを使用`extern "C"`して、装飾名*internal_name*を使用するか、エクスポートされた関数を定義する必要があります。 また、コンパイラは、 [__stdcall](../../cpp/stdcall.md)の呼び出し規約を使用する C 関数も、\_アンダースコア () のプレフィックスと、アットマーク (\@) と、引数リストのバイト数 (10 進数) で構成されるサフィックスを装飾します。

コンパイラによって生成された装飾名を検索するには、 [DUMPBIN](dumpbin-reference.md)ツールまたはリンカーの[/map](map-generate-mapfile.md)オプションを使用します。 装飾名はコンパイラ固有です。 装飾名を .DEF ファイルにエクスポートする場合、DLL にリンクする実行可能ファイルも同じバージョンのコンパイラを使用してビルドする必要があります。 これにより、呼び出し元の装飾名は .DEF ファイルのエクスポート名と一致します。

*序数*を使用\@して、関数名ではなく数値が DLL のエクスポートテーブルに入るように指定できます。 多くの Windows DLL で、レガシ コードをサポートするために序数がエクスポートされます。 DLL のサイズを最小限に抑えるのに役立つため、16 ビットの Windows コードでは序数を使用することが一般的でした。 レガシ サポートのために DLL のクライアントで必要な場合を除き、関数を序数でエクスポートすることはお勧めしません。 .LIB ファイルには序数と関数のマッピングが含まれているため、DLL を使用するプロジェクトでは通常と同様に関数名を使用できます。

**省略可能**な型のキーワードを使用することにより、序数のみでエクスポートし、結果の DLL でエクスポートテーブルのサイズを小さくすることができます。 ただし、DLL で[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)を使用する場合は、名前が有効ではないため、序数を把握しておく必要があります。

省略可能なキーワード**PRIVATE**は、 *ENTRYNAME*が、リンクによって生成されるインポートライブラリに含まれないようにします。 同じく LINK によって生成されるイメージ内のエクスポートには影響しません。

省略可能なキーワード**DATA**は、エクスポートがコードではなくデータであることを指定します。 次の例では、`exported_global` という名前のデータ変数をエクスポートする方法を示します。

```DEF
EXPORTS
   exported_global DATA
```

定義をエクスポートするには 4 つの方法があり、それらを推奨される順序で示します。

1. ソースコード内の[__declspec (dllexport)](../../cpp/dllexport-dllimport.md)キーワード

1. .DEF ファイルでの `EXPORTS` ステートメント

1. リンクコマンドでの[/export](export-exports-a-function.md)の指定

1. ソースコード内のの形式`#pragma comment(linker, "/export: definition ")`の [comment](../../preprocessor/comment-c-cpp.md) ディレクティブ。 次の例は、関数宣言`PlainFuncName`の前の #pragma コメントディレクティブを示して`_PlainFuncName@4`います。は非装飾名で、は関数の装飾名です。

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

#Pragma ディレクティブは、装飾されていない関数名をエクスポートする必要があり、ビルド構成 (たとえば、32ビットまたは64ビットのビルド) に応じて異なるエクスポートを持つ場合に便利です。

同じプログラムで 4 つの方法すべてを使用できます。 エクスポートを含むプログラムが LINK によってビルドされる際に、ビルドで .EXP ファイルが使用されていない限り、インポート ライブラリも作成されます。

次に、EXPORTS セクションの例を示します。

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

.DEF ファイルを使用して DLL から変数をエクスポートする場合、変数に `__declspec(dllexport)` を指定する必要はありません。 ただし、DLL を使用するファイルでは、データの宣言で `__declspec(dllimport)` を引き続き使用する必要があります。

## <a name="see-also"></a>関連項目

[モジュール定義ステートメントに関する規則](rules-for-module-definition-statements.md)
