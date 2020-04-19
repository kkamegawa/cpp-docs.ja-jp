---
title: IDL 属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 29761d814505d2c2dd435d3416fe2367e1c16073
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448407"
---
# <a name="idl-attributes"></a>IDL 属性

これまでは、.idl ファイルの管理のものを持っています。

- 構造とそれを変更できる .idl ファイルの構文を理解します。

- .Idl ファイルの一部の側面を変更することができますが、ウィザードに依存します。

ここで、Visual C の IDL 属性を使用してソース コード ファイル内から .idl ファイルを変更できます。 多くの場合は、Visual C の IDL 属性は、MIDL 属性と同じ名前を付けます。 Visual C の IDL 属性と MIDL 属性の名前が同じで、その設立 MIDL 属性を含む .idl ファイル内、ソース コード ファイル内の Visual C 属性を配置することが発生することを示します。 ただし、Visual C の IDL 属性では、MIDL 属性のすべての機能が提供しない可能性があります。

と共に使用しない場合[COM 属性](com-attributes.md)、IDL 属性を使用して、インターフェイスを定義できます。 ソース コードをコンパイルすると、属性は、生成された .idl ファイルの定義に使用されます。 ATL プロジェクトで COM 属性と共に使用するといくつかの IDL などの属性、`coclass`プロジェクトに挿入するコードが発生します。

なお[idl_quote](idl-quote.md)ビジュアルの現在のバージョンでサポートされていない MIDL コンストラクトを使用するとC++します。 これと他の属性など[importlib](importlib.md)と[includelib](includelib-cpp.md) 、現在の Visual Studio での既存の .idl ファイルを使用するのに役立つC++プロジェクト。

|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|別のコントロールでコントロールを集計できることを示します。|
|[appobject](appobject.md)|EXE の完全なアプリケーションに関連付けられ、関数と、コクラスのプロパティがグローバルに使用できるこのタイプ ライブラリを示しますアプリケーション オブジェクトとしてコクラスを識別します。|
|[async_uuid](async-uuid.md)|同期および非同期の両方のバージョンの COM インターフェイスを定義する、MIDL コンパイラに指示する UUID を指定します。|
|[bindable](bindable.md)|プロパティがデータ バインディングをサポートすることを示します。|
|[call_as](call-as.md)|リモート関数にマップするリモート処理不可能関数を使用できます。|
|[case](case-cpp.md)|使用される、 [switch_type](switch-type.md)共用体の属性。|
|[coclass](coclass.md)|クラスとしてコクラスを .idl ファイルに定義の場所。|
|[control](control.md)|コントロールに、ユーザー定義型を指定します。|
|[cpp_quote](cpp-quote.md)|生成されたヘッダー ファイルに、引用符なしの指定した文字列を出力します。|
|[defaultbind](defaultbind.md)|オブジェクトを最もよく表す単一のバインド可能なプロパティを示します。|
|[defaultcollelem](defaultcollelem.md)|Visual Basic コードの最適化に使用されます。|
|[defaultvalue](defaultvalue.md)|型指定された省略可能なパラメーターの既定値を指定をできます。|
|[default](default-cpp.md)|コクラス内で定義されるカスタムまたはディスパッチ インターフェイスが既定のプログラミング インターフェイスを表すことを示します。|
|[defaultvtable](defaultvtable.md)|コントロールの既定の vtable インターフェイスとしてインターフェイスを定義します。|
|[dispinterface](dispinterface.md)|ディスパッチ インターフェイスとしてインターフェイスを .idl ファイルに配置します。|
|[displaybind](displaybind.md)|バインド可能なユーザーに表示されるプロパティを示します。|
|[dual](dual.md)|.Idl ファイルにデュアル インターフェイスとしてインターフェイスを配置します。|
|[entry](entry.md)|DLL 内のエントリ ポイントを識別することによって、モジュールで、エクスポートされた関数または定数を指定します。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[helpcontext](helpcontext.md)|ユーザーがヘルプ ファイル内のこの要素についての情報を表示できるようにコンテキスト ID を指定します。|
|[helpfile](helpfile.md)|タイプ ライブラリのヘルプ ファイルの名前を設定します。|
|[helpstringcontext](helpstringcontext.md)|.Hlp または .chm ファイルをヘルプ トピックの ID を指定します。|
|[helpstringdll](helpstringdll.md)|使用してドキュメントの文字列の検索 (ローカライズ) を実行する DLL の名前を指定します。|
|[helpstring](helpstring.md)|適用先となる要素を記述するために使用される文字列を指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[idl_module](idl-module.md)|DLL エントリ ポイントを指定します。|
|[idl_quote](idl-quote.md)|IDL 構造を現在のバージョンの Visual C でサポートされていないまたは属性を使用することができます。|
|[ID](id.md)|メンバー関数 (プロパティまたはメソッド、インターフェイスまたは dispinterface) のように DISPID を指定します。|
|[iid_is](iid-is.md)|インターフェイス ポインターによって示される COM インターフェイスの IID を指定します。|
|[immediatebind](immediatebind.md)|データ バインド オブジェクトのプロパティに対するすべての変更のデータベースに直ちに通知されることを示します。|
|[importlib](importlib.md)|既に他のタイプ ライブラリでコンパイル済みの型を、作成中のタイプ ライブラリで使用できるようにします。|
|[import](import.md)|メイン .idl ファイルから参照する定義を含む .idl、.odl ファイル、またはヘッダーの別のファイルを指定します。|
|[include](include-cpp.md)|生成された .idl ファイルに含まれる 1 つまたは複数のヘッダー ファイルを指定します。|
|[includelib](includelib-cpp.md)|生成された .idl ファイルに含まれる、.idl ファイルまたは .h ファイル。|
|[in](in-cpp.md)|呼び出し元のプロシージャから呼び出されたプロシージャに渡されるパラメーターがあることを示します。|
|[last_is](last-is.md)|転送する最後の配列要素のインデックスを指定します。|
|[lcid](lcid.md)|ロケール識別子を関数に渡すことができます。|
|[length_is](length-is.md)|転送する配列要素の数を指定します。|
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
|[propputref](propputref.md)|値の代わりに参照を使用するプロパティ設定関数を指定します。|
|[propput](propput.md)|プロパティ設定関数を指定します。|
|[ptr](ptr.md)|完全なポインターとしてのポインターを指定します。|
|[public](public-cpp-attributes.md)|.Idl ファイル内から参照されていない場合でも、typedef がタイプ ライブラリに送られるようにします。|
|[range](range-cpp.md)|引数または値を持つが実行時に設定されているフィールドに使用できる値の範囲を指定します。|
|[readonly](readonly-cpp.md)|変数への代入を禁止します。|
|[ref](ref-cpp.md)|参照ポインターを識別します。|
|[requestedit](requestedit.md)|`OnRequestEdit` 通知がプロパティでサポートされることを示します。|
|[restricted](restricted.md)|あるライブラリ、またはモジュール、インターフェイス、またはディスパッチ インターフェイスのメンバーを呼び出せないことを指定します。|
|[retval](retval.md)|メンバーの戻り値を受け取るパラメーターを指定します。|
|[size_is](size-is.md)|メモリのサイズがサイズのポインターに割り当てられた、サイズのポインター、および 1 次元または多次元配列へのポインターのサイズを指定します。|
|[source](source-cpp.md)|クラス、プロパティ、またはメソッドのメンバーがイベントの発生元であることを示します。|
|[string](string-cpp.md)|示します、1 次元**char**、 **wchar_t**、 `byte`、または同等の配列またはそのような配列へのポインターは、文字列として扱う必要があります。|
|[switch_is](switch-is.md)|式または共用体の判別共用体のメンバーを選択するとして機能する識別子を指定します。|
|[switch_type](switch-type.md)|共用体の判別式として使用される変数の型を識別します。|
|[transmit_as](transmit-as.md)|提示された種類、クライアントとサーバー アプリケーションは、次の操作、転送の型との関連付けをコンパイラに指示します。|
|[uidefault](uidefault.md)|型情報メンバーは、ユーザー インターフェイスに表示する既定のメンバーであることを示します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|
|[usesgetlasterror](usesgetlasterror.md)|その関数を呼び出すときにエラーがある場合、呼び出し元できますし、呼び出しを呼び出し元に通知`GetLastError`エラー コードを取得します。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|
|[v1_enum](v1-enum.md)|指定した列挙型は、16 ビットの既定ではなく、32 ビットのエンティティとして送信するよう指示します。|
|[vararg](vararg.md)|関数が可変個の引数を実行することを指定します。|
|[vi_progid](vi-progid.md)|ProgID のバージョンに依存しない形式を指定します。|
|[wire_marshal](wire-marshal.md)|アプリケーションに固有のデータ型ではなく転送されるデータ型を指定します。|

## <a name="see-also"></a>関連項目

[グループ別の属性](attributes-by-group.md)
