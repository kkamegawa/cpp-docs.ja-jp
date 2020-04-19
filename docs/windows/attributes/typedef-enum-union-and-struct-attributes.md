---
title: Typedef、Enum、Union、および struct 型の属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 2b56ada13a0c597866d538991ed1e83078924ac9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407225"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union、および Struct 型の属性

次の属性を適用する、 [typedef](../../cpp/aliases-and-typedefs-cpp.md)、[構造体](../../cpp/struct-cpp.md)、および[列挙](../../cpp/enumerations-cpp.md)C++ のキーワード。

### <a name="typedef"></a>Typedef

|属性|説明|
|---------------|-----------------|
|[case](case-cpp.md)|使用される、 [switch_type](switch-type.md)属性、**union**します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[helpcontext](helpcontext.md)|ユーザーがヘルプ ファイル内のこの要素についての情報を表示できるようにコンテキスト ID を指定します。|
|[helpfile](helpfile.md)|タイプ ライブラリのヘルプ ファイルの名前を設定します。|
|[helpstring](helpstring.md)|適用先となる要素を記述するために使用される文字列を指定します。|
|[library_block](library-block.md)|.Idl ファイルのライブラリ ブロック内で構成要素を配置します。|
|[ptr](ptr.md)|完全なポインターとしてのポインターを指定します。|
|[public](public-cpp-attributes.md)|.Idl ファイル内から参照されていない場合でも、typedef がタイプ ライブラリに送られるようにします。|
|[ref](ref-cpp.md)|参照ポインターを識別します。|
|[switch_is](switch-is.md)|式または共用体の判別共用体のメンバーを選択するとして機能する識別子を指定します。|
|[switch_type](switch-type.md)|共用体の判別式として使用される変数の型を識別します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|
|[wire_marshal](wire-marshal.md)|アプリケーションに固有のデータ型ではなく転送されるデータ型を指定します。|

### <a name="enum"></a>enum

|属性|説明|
|---------------|-----------------|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|
|[v1_enum](v1-enum.md)|指定した列挙型は、16 ビットの既定ではなく、32 ビットのエンティティとして送信するよう指示します。|

### <a name="union"></a>union

|属性|説明|
|---------------|-----------------|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[last_is](last-is.md)|転送する最後の配列要素のインデックスを指定します。|
|[length_is](length-is.md)|転送する配列要素の数を指定します。|
|[max_is](max-is.md)|有効な配列のインデックスの最大値を指定します。|
|[size_is](size-is.md)|メモリのサイズがサイズのポインターに割り当てられた、サイズのポインター、および 1 次元または多次元配列へのポインターのサイズを指定します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|

### <a name="nonencapsulated-union"></a>カプセル化されていない共用体

|属性|説明|
|---------------|-----------------|
|[ms_union](ms-union.md)|カプセル化されていない共用体のネットワーク データ表現の整列を制御します。|
|[no_injected_text](no-injected-text.md)|コンパイラがコードの属性を使用した結果として挿入するを防ぎます。|

### <a name="struct"></a>struct

|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|クラスは、集計をサポートしていることを示します。|
|[aggregates](aggregates.md)|コントロールがターゲット クラスを集約することを示します。|
|[appobject](appobject.md)|完全な .exe アプリケーションに関連付けられ、関数と、コクラスのプロパティがグローバルに使用できるこのタイプ ライブラリを示しますアプリケーション オブジェクトとしてコクラスを識別します。|
|[coclass](coclass.md)|ActiveX コントロールを作成します。|
|[com_interface_entry](com-interface-entry-cpp.md)|COM マップには、インターフェイスのエントリを追加します。|
|[control](control.md)|コントロールに、ユーザー定義型を指定します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[db_column](db-column.md)|行セットに指定された列をバインドします。|
|[db_command](db-command.md)|OLE DB コマンドを作成します。|
|[db_param](db-param.md)|入力または出力パラメーターを使用して、指定したメンバー変数を関連付けるし、変数を区切ります。|
|[db_source](db-source.md)|データ ソースへの接続を作成します。|
|[db_table](db-table.md)|OLE DB、テーブルを開きます。|
|[default](default-cpp.md)|コクラス内で定義されるカスタムまたはディスパッチ インターフェイスが既定のプログラミング インターフェイスを表すことを示します。|
|[defaultvtable](defaultvtable.md)|コントロールの既定の vtable インターフェイスとしてインターフェイスを定義します。|
|[event_receiver](event-receiver.md)|イベント レシーバーを作成します。|
|[event_source](event-source.md)|イベント ソースを作成します。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[implements_category](implements-category.md)|クラスの実装されたコンポーネントのカテゴリを指定します。|
|[last_is](last-is.md)|転送する最後の配列要素のインデックスを指定します。|
|[length_is](length-is.md)|転送する配列要素の数を指定します。|
|[max_is](max-is.md)|有効な配列のインデックスの最大値を指定します。|
|[requires_category](requires-category.md)|ターゲット クラスの必須コンポーネントのカテゴリを指定します。|
|[size_is](size-is.md)|メモリのサイズがサイズのポインターに割り当てられた、サイズのポインター、および 1 次元または多次元配列へのポインターのサイズを指定します。|
|[source](source-cpp.md)|クラスの場合、接続ポイント用の COM オブジェクトのソース インターフェイスを指定します。 プロパティまたはメソッドでは、オブジェクトまたはイベントのソースをバリアントにメンバーを返すことを示します。|
|[threading](threading-cpp.md)|COM オブジェクトのスレッド モデルを指定します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|
|[version](version-cpp.md)|クラスの複数のバージョン間で特定のバージョンを識別します。|
|[vi_progid](vi-progid.md)|ProgID のバージョンに依存しない形式を指定します。|

## <a name="see-also"></a>関連項目

[使用法別の属性](attributes-by-usage.md)