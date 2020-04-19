---
title: '#import ディレクティブ (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220268"
---
# <a name="import-directive-c"></a>#import ディレクティブ (C++)

**C++のみ**

タイプ ライブラリからの情報を組み込むために使用します。 タイプ ライブラリの内容は、ほとんどが COM インターフェイスを記述した C++ クラスに変換されます。

## <a name="syntax"></a>構文

> **#import**"*filename*" \[*属性*] \
> **#import**\<*ファイル*名属性> ]\[

### <a name="parameters"></a>パラメーター

*/db*\
インポートするタイプ ライブラリ ファイルを指定します。 *ファイル名*は、次のいずれかの種類にすることができます。

- .olb、.tlb、.dll ファイルなど、タイプ ライブラリを含むファイルの名前。 キーワード`file:`は、各ファイル名の前に置くことができます。

- タイプ ライブラリのコントロールの progid。 キーワード`progid:`は、各 progid の前に置くことができます。 例えば:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Progid の詳細については、「[ローカライズ ID とバージョン番号の指定](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)」を参照してください。

   64ビットオペレーティングシステムで32ビットクロスコンパイラを使用する場合、コンパイラは32ビットレジストリハイブのみを読み取ることができます。 ネイティブ 64 ビット コンパイラを使用して、64 ビットのタイプ ライブラリをビルドおよび登録した方がよい場合があります。

- タイプ ライブラリのライブラリ ID。 キーワード`libid:`は、各ライブラリ ID の前に置くことができます。 例えば:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   または`version` `libid:` `progid:`を指定しない場合は、に適用される[規則](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)がにも適用されます。`lcid`

- 実行可能 (.exe) ファイル。

- タイプライブラリリソース (.ocx など) を含むライブラリ (.dll) ファイル。

- タイプ ライブラリを保持する複合ドキュメント。

- **Loadtypelib** API で認識できるその他のファイル形式。

*アトリビュート*\
1つまたは複数の[#import 属性](#_predir_the_23import_directive_import_attributes)。 複数の属性を指定するときは、空白またはコンマで区切ります。 例:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- または -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Remarks

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>ファイル名の検索順序

*ファイル名*の前にディレクトリ指定が必要です。 そのファイル名は既存のファイルの名前であることが必要です。 2 つの構文形式間の違いは、パスの指定が不完全であるときに、プリプロセッサがタイプ ライブラリ ファイルを検索する順序です。

|構文形式|アクション|
|-----------------|------------|
|引用符形式|プリプロセッサに対して、 **#import**ステートメントを含むファイルのディレクトリにあるタイプライブラリファイルを検索するように指示します。次に、そのファイル`#include`が含まれているファイル () のディレクトリで、そのファイルを検索します。 プリプロセッサは次のパスに従って検索します。|
|山かっこ形式|プリプロセッサに次のパスに従ってタイプ ライブラリ ファイルを検索するように指示します。<br /><br /> 1.環境`PATH`変数のパスリスト<br />2.環境`LIB`変数のパスリスト<br />3.[/I](../build/reference/i-additional-include-directories.md)コンパイラオプションで指定されたパス。ただし、コンパイラは、 [no_registry](../preprocessor/no-registry.md)属性を使用して別のタイプライブラリから参照されたタイプライブラリを検索します。|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>ローカライズ ID とバージョン番号を指定します

progid を指定するときに、progid のローカリゼーション ID とバージョン番号も指定できます。 例えば:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

ローカライズ ID を指定しない場合、progid は次の規則に従って選択されます。

- ローカライズ ID が1つしかない場合は、その ID が使用されます。

- 複数のローカライズ ID がある場合は、バージョン番号が0、9、または409の最初の ID が使用されます。

- ローカライズ ID が複数あり、そのいずれも0、9、または409ではない場合は、最後の ID が使用されます。

- バージョン番号を指定しない場合は、最新のバージョンが使用されます。

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>インポートによって作成されるヘッダーファイル

**#import**は、ソースコード内のC++タイプライブラリの内容を再構築する2つのヘッダーファイルを作成します。 プライマリヘッダーファイルは、Microsoft インターフェイス定義言語 (MIDL) コンパイラによって生成されるものと似ていますが、コンパイラによって生成されるコードとデータが追加されています。 [プライマリヘッダーファイル](#_predir_the_primary_type_library_header_file)には、タイプライブラリと同じ基本名とが含まれています。TLH 拡張。 セカンダリ ヘッダー ファイルには、タイプ ライブラリと同じ基本名と .TLI 拡張子が付けられます。 このファイルは、コンパイラが生成したメンバー関数の実装を格納しており、プライマリ ヘッダー ファイルにインクルード (`#include`) されます。

パラメーターを使用`byref`するディスパッチインターフェイスプロパティをインポートする場合、 **#import**は関数の[__declspec (property)](../cpp/property-cpp.md)ステートメントを生成しません。

両方のヘッダーファイルは、 [/fo (name object file)](../build/reference/fo-object-file-name.md)オプションで指定された出力ディレクトリに配置されます。 次に、プライマリヘッダーファイルに`#include`ディレクティブで名前が付けられているかのように、コンパイラによって読み取られ、コンパイルされます。

次のコンパイラの最適化には、 **#import**ディレクティブが付属しています。

- ヘッダー ファイルは作成時にタイプ ライブラリと同じタイムスタンプが付けられます。

- **#Import**が処理されると、コンパイラはまずヘッダーが存在し、最新の状態であるかどうかを確認します。 そうであれば、再作成する必要はありません。

**#Import**ディレクティブも最小リビルドに関与し、プリコンパイル済みヘッダーファイルに配置できます。  詳細については、「[プリコンパイル済みヘッダーファイルの作成](../build/creating-precompiled-header-files.md)」を参照してください。

### <a name="_predir_the_primary_type_library_header_file"></a>プライマリタイプライブラリのヘッダーファイル

プライマリ タイプ ライブラリのヘッダー ファイルは、7 つのセクションで構成されます。

- 見出しの定型:コメント、 `#include` comdef のステートメントで構成されます。H (ヘッダーで使用される標準マクロを定義する) とその他の設定情報。

- 前方参照と typedef:`struct IMyInterface`や typedef などの構造体の宣言で構成されます。

- スマートポインターの宣言:このテンプレートクラス`_com_ptr_t`はスマートポインターです。 インターフェイスポインターをカプセル化することで、 `AddRef` `Release`、、および`QueryInterface`の各関数を呼び出す必要がなくなります。 また、新しい COM `CoCreateInstance`オブジェクトを作成するときに呼び出しを非表示にします。 このセクションでは、マクロ`_COM_SMARTPTR_TYPEDEF`ステートメントを使用して、 [_com_ptr_t](../cpp/com-ptr-t-class.md)テンプレートクラスのテンプレートの特殊化として COM インターフェイスの typedef を確立します。 たとえば、インターフェイス`IMyInterface`の場合は、のようになります。TLH ファイルには次のものが含まれます。

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   コンパイラが次のように展開します。

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   `IMyInterfacePtr` 型は、未加工のインターフェイス ポインター `IMyInterface*` の代わりに使用できます。 そのため、さまざまな`IUnknown`メンバー関数を呼び出す必要はありません。

- Typeinfo 宣言:は、主にによって`ITypeLib:GetTypeInfo`返される個々の typeinfo 項目を公開するクラス定義とその他の項目で構成されます。 このセクションでは、型ライブラリの各 typeinfo は、`TYPEKIND` 情報に応じてヘッダーに反映されます。

- 省略可能な旧形式の GUID の定義:名前付き GUID 定数の初期化を含みます。 これらの名前の形式`CLSID_CoClass`は`IID_Interface`、MIDL コンパイラによって生成されるものと同様です。

- セカンダリ タイプ ライブラリ ヘッダーの `#include` ステートメント。

- フッターの定型:現在は`#pragma pack(pop)`が含まれています。

見出しの定型句とフッターの定型句を除くすべてのセクションは、元の IDL ファイルの`library`ステートメントで指定された名前を持つ名前空間で囲まれています。 タイプライブラリヘッダーの名前は、名前空間名を使用した明示的な修飾によって使用できます。 または、次のステートメントを含めることができます。

```cpp
using namespace MyLib;
```

ソースコード内の **#import**ステートメントの直後。

名前空間は、 **#import**ディレクティブの[no_namespace](no-namespace.md)) 属性を使用して抑制できます。 ただし、名前空間を抑制すると、名前の競合が発生する場合があります。 名前空間は、 [rename_namespace](rename-namespace.md)属性によって名前を変更することもできます。

コンパイラは、現在処理しているタイプライブラリに必要なタイプライブラリの依存関係への完全なパスを提供します。 パスは、処理されたタイプ ライブラリごとにコンパイラが生成するタイプ ライブラリ ヘッダー (.TLH) に、コメントの形式で記述されます。

タイプ ライブラリに他のタイプ ライブラリで定義された型への参照が含まれている場合は、.TLH ファイルに次の種類のコメントが含まれます。

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#Import**コメント内の実際のファイル名は、レジストリに格納されている、相互参照されるタイプライブラリの完全なパスです。 型定義が存在しないことが原因でエラーが発生した場合は、の先頭にあるコメントを確認してください。TLH を使用すると、最初にインポートする必要がある依存タイプライブラリを確認できます。 .TLI ファイルのコンパイル中に考えられるエラーは、構文エラー (C2143、C2146、C2321 など)、C2501 (decl-specifier の欠落)、または C2433 (データ宣言子内でのインライン禁止) です。

依存関係エラーを解決するには、システムヘッダーによって提供されない依存関係コメントを確認し、依存タイプライブラリの **#import**ディレクティブの前にある時点で **#import**ディレクティブを指定します。

### <a name="_predir_the_23import_directive_import_attributes"></a>#import 属性

**#import**には、必要に応じて1つ以上の属性を含めることができます。 これらの属性は、コンパイラにタイプ ライブラリ ヘッダーの内容を変更するように指示します。 円記号 ( **\\** ) を使用すると、1つの **#import**ステートメントに追加の行を含めることができます。 例えば:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

詳細については、「[属性の #import](../preprocessor/hash-import-attributes-cpp.md)」を参照してください。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)\
[コンパイラの COM サポート](../cpp/compiler-com-support.md)
