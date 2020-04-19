---
title: '#インポート属性 (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 7e0de241bd27269d7d758c49bc54c4bf435cf383
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220095"
---
# <a name="import-attributes-c"></a>#import の属性C++()

`#import`ディレクティブで使用される属性へのリンクを示します。

**Microsoft 固有の仕様**

`#import`ディレクティブでは、次の属性を使用できます。

|属性|説明|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|潜在的な名前の競合を解決するため、変数名に 2 つのアンダースコア (__) を追加して C++ の予約語の名前を変更します。|
|[auto_search](../preprocessor/auto-search.md)|タイプ ライブラリが #import を使用して参照され、自身が別のタイプ ライブラリを参照している場合、コンパイラが他のタイプ ライブラリに対して暗黙の #import を実行できることを指定します。|
|[embedded_idl](../preprocessor/embedded-idl.md)|属性が生成されたコードを保持して、タイプ ライブラリを .tlh ファイルに書き込むことを指定します。|
|[exclude](../preprocessor/exclude-hash-import.md)|生成されるタイプ ライブラリのヘッダー ファイルから項目を除外します。|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|高レベルのプロパティおよびメソッドの名前付けで使用されるプレフィックスを指定します。|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|3 つのプロパティ メソッドの代替プレフィックスを指定します。|
|[implementation_only](../preprocessor/implementation-only.md)|.tlh ヘッダー ファイル (プライマリ ヘッダー ファイル) の生成を抑制します。|
|[include()](../preprocessor/include-parens.md)|自動除外を無効にします。|
|[inject_statement](../preprocessor/inject-statement.md)|タイプ ライブラリ ヘッダーに引数をソース テキストとして挿入します。|
|[named_guids](../preprocessor/named-guids.md)|、、 `LIBID_MyLib` `IID_MyInterface`、 `CLSID_MyCoClass`および`DIID_MyDispInterface`の形式の古いスタイルで GUID 変数を定義および初期化するようコンパイラに指示します。|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|自動除外を無効にします。|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|コンパイラがデュアル インターフェイス メソッドのラッパー関数を生成する方法を変更します。|
|[no_implementation](../preprocessor/no-implementation.md)|ラッパー メンバー関数の実装を含む .tli ヘッダーの生成を抑制します。|
|[no_namespace](../preprocessor/no-namespace.md)|名前空間名がコンパイラによって生成されないことを指定します。|
|[no_registry](../preprocessor/no-registry.md)|タイプ ライブラリのレジストリを検索しないようコンパイラに指示します。|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|には[no_namespace](../preprocessor/no-namespace.md)属性と同じ機能がありますが、型ライブラリでは、 [auto_search](../preprocessor/auto-search.md)属性を持つ #import ディレクティブを使用します。|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|タイプ ライブラリのすべてのインターフェイスに対して、スマート ポインターの作成を抑制します。|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|は、を呼び出し`IDispatch::Invoke`て HRESULT エラーコードを返すディスパッチインターフェイスのメソッドとプロパティに対して低レベルのラッパー関数を生成するようコンパイラに指示します。|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|では、これらのラッパー関数を使用するエラー処理ラッパー関数と[プロパティ](../cpp/property-cpp.md)宣言が生成されません。|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|名前の衝突を避けるために異なるプレフィックスを指定します。|
|[raw_native_types](../preprocessor/raw-native-types.md)|高レベルのラッパー関数の COM サポート クラスの使用を無効にし、代わりに低レベルのデータ型の使用を強制します。|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|3 つのプロパティ メソッドの代替プレフィックスを指定します。|
|[rename](../preprocessor/rename-hash-import.md)|名前の衝突の問題を回避します。|
|[rename_namespace](../preprocessor/rename-namespace.md)|タイプ ライブラリの内容を含む名前空間の名前を変更します。|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|には[rename_namespace](../preprocessor/rename-namespace.md)属性と同じ機能がありますが、型ライブラリでは、 [auto_search](../preprocessor/auto-search.md)属性を持つ #import ディレクティブを使用します。|
|[tlbid](../preprocessor/tlbid.md)|プライマリ タイプ ライブラリ以外のライブラリの読み込みを許可します。|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)