---
title: CString の基本操作
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: 08c496038efc9e24e1c1610da07b6824c3a50b64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216858"
---
# <a name="basic-cstring-operations"></a>CString の基本操作

このトピックの次の基本的な[CString](../atl-mfc-shared/reference/cstringt-class.md)操作。

- [標準 C リテラル文字列を CString オブジェクトの作成](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [CString の個々 の文字へのアクセス](#_core_accessing_individual_characters_in_a_cstring)

- [2 つの CString オブジェクトを連結します。](#_core_concatenating_two_cstring_objects)

- [CString オブジェクトの比較](#_core_comparing_cstring_objects)

- [CString オブジェクトに変換します。](#_core_converting_cstring_objects)

`Class CString` クラス テンプレートに基づく[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)します。 `CString` **typedef**の`CStringT`します。 正確には、`CString`は、 **typedef**の*明示的な特殊化*の`CStringT`クラスを定義するクラス テンプレートを使用する一般的な方法であります。 同様に定義されたクラスは、`CStringA`と`CStringW`します。

`CString`、 `CStringA`、および`CStringW`atlstr.h で定義されます。 `CStringT` cstringt.h で定義されます。

`CString`、 `CStringA`、と`CStringW`メソッドとで定義された演算子のセットを取得各`CStringT`サポートされる文字列データで使用するためです。 C ランタイム ライブラリの文字列のサービスと重複して、場合によっては、メソッドの一部になります。

注:`CString`ネイティブ クラスです。 C++ で使用される文字列クラスの/cli プロジェクトを使用してマネージ`System.String`します。

##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 標準 C リテラル文字列を CString オブジェクトの作成

C スタイルのリテラル文字列を割り当てることができます、`CString`いずれかを割り当てることができますよう`CString`を別のオブジェクト。

- C リテラル文字列の値を割り当てて、`CString`オブジェクト。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- いずれかの値を割り当てる`CString`間`CString`オブジェクト。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   内容を`CString`1 つのときに、オブジェクトがコピーされる`CString`オブジェクトは別に割り当てられます。 そのため、2 つの文字列では、文字列を構成する実際の文字への参照は共有されません。 使用する方法の詳細についての`CString`を値としてオブジェクトを参照してください[CString セマンティクス](../atl-mfc-shared/cstring-semantics.md)します。

   > [!NOTE]
   > Unicode または ANSI 用にコンパイルできるように、アプリケーションを作成するには、_T マクロを使用して、リテラル文字列を記述します。 詳細については、次を参照してください。 [Unicode およびマルチバイト文字セット (MBCS) のサポート](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)します。

##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> CString の個々 の文字へのアクセス

個々 の文字にアクセスすることができます、`CString`オブジェクトを使用して、`GetAt`と`SetAt`メソッド。 代わりに、配列の要素、または添字演算子 () を使用することもできます。`GetAt`を個々 の文字を取得します。 (配列の要素へのアクセスがインデックスで標準の C スタイル文字列のように似ています)値をインデックス`CString`文字は 0 から始まります。

##  <a name="_core_concatenating_two_cstring_objects"></a> 2 つの CString オブジェクトを連結します。

2 つを連結する`CString`オブジェクト、連結演算子を使用して、(+ や + =)、次のようにします。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

連結演算子を少なくとも 1 つの引数 (+ + = または) する必要があります、`CString`文字列定数を使用できますが、オブジェクト (たとえば、 `"big"`) または**char** (たとえば、' x')、他の引数の。

##  <a name="_core_comparing_cstring_objects"></a> CString オブジェクトの比較

`Compare`メソッドと演算子 = =`CString`は同等です。 `Compare`、**演算子 = =**、および`CompareNoCase`は MBCS および Unicode が対応しています。`CompareNoCase`大文字小文字が区別もします。 `Collate`メソッドの`CString`ロケールに依存するは、多くの場合よりも低速`Compare`します。 使用`Collate`現在のロケールで指定されたルールを並べ替え、遵守すべき場所にのみです。

次の表は、使用可能な[CString](../atl-mfc-shared/reference/cstringt-class.md)比較関数と C ランタイム ライブラリで同等の Unicode と MBCS ポータブル関数。

|CString 関数|MBCS 関数|Unicode 関数|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`クラス テンプレートが関係演算子を定義します (<、 \<=、> =、>、= =、! =) で使用するために利用可能な`CString`します。 2 つを比較する`CStrings`の次の例に示すように、これらの演算子を使用しています。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

##  <a name="_core_converting_cstring_objects"></a> CString オブジェクトに変換します。

CString オブジェクトを他の文字列型に変換する方法の詳細については、次を参照してください。[方法。さまざまな文字列型の間で変換](../text/how-to-convert-between-various-string-types.md)します。

## <a name="using-cstring-with-wcout"></a>Wcout での CString の使用

CString を使用する`wcout`にオブジェクトを明示的にキャストする必要があります、`const wchar_t*`次の例に示すように。

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

キャストなし`cs`として扱われますが、`void*`と`wcout`オブジェクトのアドレスを出力します。 この動作は、C++ の標準に準拠して正しい自体がテンプレート引数の推論とオーバー ロード解決の間の微妙な相互作用によって発生します。

## <a name="see-also"></a>関連項目

[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[クラス テンプレートの部分的特殊化](../cpp/template-specialization-cpp.md)<br/>
[方法: さまざまな文字列型間で変換する](../text/how-to-convert-between-various-string-types.md)
