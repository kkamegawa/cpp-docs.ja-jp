---
title: 属性リファレンス (アルファベット順)
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: 386afe5362f876cd1489a35839f4f8cfc2381e91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148498"
---
# <a name="attributes-alphabetical-reference"></a>属性リファレンス (アルファベット順)

次の属性は、Microsoft C コンパイラで使用できます。

|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|別のコントロールでコントロールを集計できることを示します。|
|[aggregates](aggregates.md)|コントロールがターゲット クラスを集約することを示します。|
|[appobject](appobject.md)|EXE の完全なアプリケーションに関連付けられ、関数と、コクラスのプロパティがグローバルに使用できるこのタイプ ライブラリを示しますアプリケーション オブジェクトとしてコクラスを識別します。|
|[async_uuid](async-uuid.md)|同期および非同期の両方のバージョンの COM インターフェイスを定義する、MIDL コンパイラに指示する UUID を指定します。|
|[attribute](attribute.md)|カスタム属性を作成することができます。|
|[bindable](bindable.md)|プロパティがデータ バインディングをサポートすることを示します。|
|[call_as](call-as.md)|リモート関数にマップするリモート処理不可能関数を使用できます。|
|[case](case-cpp.md)|使用される、 [switch_type](switch-type.md)共用体の属性。|
|[coclass](coclass.md)|COM インターフェイスを実装できる COM オブジェクトを作成します。|
|[com_interface_entry](com-interface-entry-cpp.md)|COM マップには、インターフェイスのエントリを追加します。|
|[control](control.md)|コントロールに、ユーザー定義型を指定します。|
|[cpp_quote](cpp-quote.md)|生成されたヘッダー ファイルに、引用符なしの指定した文字列を出力します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[db_accessor](db-accessor.md)|行セットの列をバインドし、対応するアクセサー マップにバインドします。|
|[db_column](db-column.md)|行セットに指定された列をバインドします。|
|[db_command](db-command.md)|OLE DB コマンドを実行します。|
|[db_param](db-param.md)|指定したメンバー変数を入力または出力パラメーターに関連付けます。|
|[db_source](db-source.md)|作成し、データ ソースへのプロバイダー経由の接続をカプセル化します。|
|[db_table](db-table.md)|OLE DB、テーブルを開きます。|
|[default](default-cpp.md)|コクラス内で定義されるカスタムまたはディスパッチ インターフェイスが既定のプログラミング インターフェイスを表すことを示します。|
|[defaultbind](defaultbind.md)|オブジェクトを最もよく表す単一のバインド可能なプロパティを示します。|
|[defaultcollelem](defaultcollelem.md)|Visual Basic コードの最適化に使用されます。|
|[defaultvalue](defaultvalue.md)|型指定された省略可能なパラメーターの既定値を指定をできます。|
|[defaultvtable](defaultvtable.md)|コントロールの既定の vtable インターフェイスとしてインターフェイスを定義します。|
|[dispinterface](dispinterface.md)|ディスパッチ インターフェイスとしてインターフェイスを .idl ファイルに配置します。|
|[displaybind](displaybind.md)|バインド可能なユーザーに表示されるプロパティを示します。|
|[dual](dual.md)|.Idl ファイルにデュアル インターフェイスとしてインターフェイスを配置します。|
|[emitidl](emitidl.md)|後続のすべての IDL 属性が処理され、生成された .idl ファイル内に配置するかどうかを判断します。|
|[entry](entry.md)|DLL 内のエントリ ポイントを識別することによって、モジュールで、エクスポートされた関数または定数を指定します。|
|[event_receiver](event-receiver.md)|イベント レシーバーを作成します。|
|[event_source](event-source.md)|イベント ソースを作成します。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[helpcontext](helpcontext.md)|ユーザーがヘルプ ファイル内のこの要素についての情報を表示できるようにコンテキスト ID を指定します。|
|[helpfile](helpfile.md)|タイプ ライブラリのヘルプ ファイルの名前を設定します。|
|[helpstring](helpstring.md)|.Hlp または .chm ファイルをヘルプ トピックの ID を指定します。|
|[helpstringdll](helpstringdll.md)|使用してドキュメントの文字列の検索 (ローカライズ) を実行する DLL の名前を指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[ID](id.md)|メンバー関数 (プロパティまたはメソッド、インターフェイスまたは dispinterface) のように DISPID を指定します。|
|[idl_module](idl-module.md)|DLL エントリ ポイントを指定します。|
|[idl_quote](idl-quote.md)|IDL 構造を現在のバージョンの Visual C でサポートされていないまたは属性を使用することができます。|
|[iid_is](iid-is.md)|インターフェイス ポインターによって示される COM インターフェイスの IID を指定します。|
|[immediatebind](immediatebind.md)|データ バインド オブジェクトのプロパティに対するすべての変更のデータベースに直ちに通知されることを示します。|
|[implements](implements-cpp.md)|IDL コクラスのメンバーであるが強制されているディスパッチ インターフェイスを指定します。|
|[implements_category](implements-category.md)|クラスの実装されたコンポーネントのカテゴリを指定します。|
|[import](import.md)|メイン .idl ファイルから参照する定義を含む .idl、.odl ファイル、またはヘッダーの別のファイルを指定します。|
|[importidl](importidl.md)|生成された .idl ファイルには、指定された .idl ファイルを挿入します。|
|[importlib](importlib.md)|既に他のタイプ ライブラリでコンパイル済みの型を、作成中のタイプ ライブラリで使用できるようにします。|
|[in](in-cpp.md)|呼び出し元のプロシージャから呼び出されたプロシージャに渡されるパラメーターがあることを示します。|
|[include](include-cpp.md)|生成された .idl ファイルに含まれる 1 つまたは複数のヘッダー ファイルを指定します。|
|[includelib](includelib-cpp.md)|生成された .idl ファイルに含まれる、.idl ファイルまたは .h ファイル。|
|[last_is](last-is.md)|転送する最後の配列要素のインデックスを指定します。|
|[lcid](lcid.md)|ロケール識別子を関数に渡すことができます。|
|[length_is](length-is.md)|転送する配列要素の数を指定します。|
|[library_block](library-block.md)|.Idl ファイルのライブラリ ブロック内で構成要素を配置します。|
|[licensed](licensed.md)|適用するコクラスはライセンスされていることを示しますを使用してインスタンス化する必要があります`IClassFactory2`します。|
|[local](local-cpp.md)|インターフェイスのヘッダーで使用する場合は、ヘッダー ジェネレーターとして、MIDL コンパイラを使用することができます。 個々 の関数で使用する場合は、スタブが生成されたないローカル プロシージャを指定します。|
|[max_is](max-is.md)|有効な配列のインデックスの最大値を指定します。|
|[module](module-cpp.md)|.idl ファイルのライブラリ ブロックを定義します。|
|[ms_union](ms-union.md)|カプセル化されていない共用体のネットワーク データ表現の整列を制御します。|
|[no_injected_text](no-injected-text.md)|コンパイラがコードの属性を使用した結果として挿入するを防ぎます。|
|[nonbrowsable](nonbrowsable.md)|インターフェイス メンバーをプロパティ ブラウザーに表示されないことを示します。|
|[noncreatable](noncreatable.md)|単独でインスタンス化できないオブジェクトを定義します。|
|[nonextensible](nonextensible.md)|指定します、`IDispatch`実装にはプロパティのみが含まれていて、メソッドは、インターフェイスの説明に記載して、実行時にメンバーを追加して拡張することはできません。|
|[object](object-cpp.md)|カスタムのインターフェイスを識別します。カスタム属性と同義です。|
|[odl](odl.md)|オブジェクト記述言語 (ODL) インターフェイスとしてインターフェイスを識別します。|
|[oleautomation](oleautomation.md)|インターフェイスが Automation と互換性があることを示します。|
|[optional](optional-cpp.md)|メンバー関数のオプション パラメーターを指定します。|
|[out](out-cpp.md)|呼び出されたプロシージャから呼び出したプロシージャ (サーバーからクライアント) に返されるポインター パラメーターを示します。|
|[pointer_default](pointer-default.md)|パラメーター リストで表示される最上位レベルのポインターを除くすべてのポインターの既定のポインターの属性を指定します。|
|[pragma](pragma.md)|生成された .idl ファイルに、引用符なしの指定した文字列を出力します。|
|[progid](progid.md)|COM オブジェクトの ProgID を指定します。|
|[propget](propget.md)|プロパティのアクセサー (get) 関数を指定します。|
|[propput](propput.md)|プロパティ設定関数を指定します。|
|[propputref](propputref.md)|値の代わりに参照を使用するプロパティ設定関数を指定します。|
|[ptr](ptr.md)|完全なポインターとしてのポインターを指定します。|
|[public](public-cpp-attributes.md)|.Idl ファイル内から参照されていない場合でも、typedef がタイプ ライブラリに送られるようにします。|
|[range](range-cpp.md)|引数または値を持つが実行時に設定されているフィールドに使用できる値の範囲を指定します。|
|[rdx](rdx.md)|作成またはレジストリ キーを変更します。|
|[readonly](readonly-cpp.md)|変数への代入を禁止します。|
|[ref](ref-cpp.md)|参照ポインターを識別します。|
|[registration_script](registration-script.md)|指定した登録スクリプトを実行します。|
|[requestedit](requestedit.md)|`OnRequestEdit` 通知がプロパティでサポートされることを示します。|
|[requires_category](requires-category.md)|クラスの必須コンポーネントのカテゴリを指定します。|
|[restricted](restricted.md)|あるライブラリ、またはモジュール、インターフェイス、またはディスパッチ インターフェイスのメンバーを呼び出せないことを指定します。|
|[retval](retval.md)|メンバーの戻り値を受け取るパラメーターを指定します。|
|[satype](satype.md)|データ型を指定します、`SAFEARRAY`します。|
|[size_is](size-is.md)|メモリのサイズがサイズのポインターに割り当てられた、サイズのポインター、および 1 次元または多次元配列へのポインターのサイズを指定します。|
|[source](source-cpp.md)|クラス、プロパティ、またはメソッドのメンバーがイベントの発生元であることを示します。|
|[string](string-cpp.md)|示します、1 次元**char**、 **wchar_t**、 `byte`、または同等の配列またはそのような配列へのポインターは、文字列として扱う必要があります。|
|[support_error_info](support-error-info.md)|ターゲット オブジェクトのエラー報告をサポートしています。|
|[switch_is](switch-is.md)|式または共用体の判別共用体のメンバーを選択するとして機能する識別子を指定します。|
|[switch_type](switch-type.md)|共用体の判別式として使用される変数の型を識別します。|
|[synchronize](synchronize.md)|メソッドへのアクセスを同期します。|
|[threading](threading-cpp.md)|COM オブジェクトのスレッド モデルを指定します。|
|[transmit_as](transmit-as.md)|提示された種類、クライアントとサーバー アプリケーションは、次の操作、転送の型との関連付けをコンパイラに指示します。|
|[uidefault](uidefault.md)|型情報メンバーは、ユーザー インターフェイスに表示する既定のメンバーであることを示します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|
|[usesgetlasterror](usesgetlasterror.md)|その関数を呼び出すときにエラーがある場合、呼び出し元できますし、呼び出しを呼び出し元に通知`GetLastError`エラー コードを取得します。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|
|[v1_enum](v1-enum.md)|指定した列挙型は、16 ビットの既定ではなく、32 ビットのエンティティとして送信するよう指示します。|
|[vararg](vararg.md)|関数が可変個の引数を実行することを指定します。|
|[version](version-cpp.md)|インターフェイスまたはクラスの複数のバージョン間で特定のバージョンを識別します。|
|[vi_progid](vi-progid.md)|ProgID のバージョンに依存しない形式を指定します。|
|[wire_marshal](wire-marshal.md)|アプリケーションに固有のデータ型ではなく転送されるデータ型を指定します。|

## <a name="see-also"></a>関連項目

[COM および .NET の C++ の属性](cpp-attributes-com-net.md)<br/>
[グループ別の属性](attributes-by-group.md)<br/>
[使用法別の属性](attributes-by-usage.md)