---
title: メソッドの属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409176"
---
# <a name="method-attributes"></a>メソッド属性

次の属性は、クラス、コクラスまたはインターフェイスのメソッドに適用されます。

|属性|説明|
|---------------|-----------------|
|[bindable](bindable.md)|プロパティがデータ バインディングをサポートすることを示します。|
|[call_as](call-as.md)|リモート関数にマップするリモート処理不可能関数を使用できます。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[db_column](db-column.md)|行セットに指定された列をバインドします。|
|[db_command](db-command.md)|OLE DB コマンドを作成します。|
|[db_param](db-param.md)|入力または出力パラメーターを使用して、指定したメンバー変数を関連付けるし、変数を区切ります。|
|[db_source](db-source.md)|データ ソースへの接続を作成します。|
|[db_table](db-table.md)|OLE DB、テーブルを開きます。|
|[defaultbind](defaultbind.md)|オブジェクトを最もよく表す単一のバインド可能なプロパティを示します。|
|[defaultcollelem](defaultcollelem.md)|Visual Basic コードの最適化に使用されます。|
|[displaybind](displaybind.md)|バインド可能なユーザーに表示されるプロパティを示します。|
|[helpcontext](helpcontext.md)|ユーザーには、この要素に関する情報を表示できるようにコンテキスト ID を指定します、**ヘルプ**ファイル。|
|[helpfile](helpfile.md)|名前を設定、**ヘルプ**タイプ ライブラリ ファイル。|
|[helpstring](helpstring.md)|適用先となる要素を記述するために使用される文字列を指定します。|
|[helpstringcontext](helpstringcontext.md)|.Hlp または .chm ファイルをヘルプ トピックの ID を指定します。|
|[helpstringdll](helpstringdll.md)|使用してドキュメントの文字列の検索 (ローカライズ) を実行する DLL の名前を指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[ID](id.md)|メンバー関数 (プロパティまたはメソッド、インターフェイスまたは dispinterface) のように DISPID を指定します。|
|[immediatebind](immediatebind.md)|データ バインド オブジェクトのプロパティに対するすべての変更のデータベースに直ちに通知されることを示します。|
|[in](in-cpp.md)|呼び出し元のプロシージャから呼び出されたプロシージャに渡されるパラメーターがあることを示します。|
|[local](local-cpp.md)|インターフェイスのヘッダーで使用する場合は、ヘッダー ジェネレーターとして、MIDL コンパイラを使用することができます。 個々 の関数で使用する場合は、スタブが生成されたないローカル プロシージャを指定します。|
|[nonbrowsable](nonbrowsable.md)|インターフェイス メンバーをプロパティ ブラウザーに表示されないことを示します。|
|[propget](propget.md)|プロパティのアクセサー関数を指定します。|
|[propput](propput.md)|プロパティ設定関数を指定します。|
|[propputref](propputref.md)|値の代わりに参照を使用するプロパティ設定関数を指定します。|
|[ptr](ptr.md)|完全なポインターとしてのポインターを指定します。|
|[range](range-cpp.md)|引数または値を持つが実行時に設定されているフィールドに使用できる値の範囲を指定します。|
|[requestedit](requestedit.md)|`OnRequestEdit` 通知がプロパティでサポートされることを示します。|
|[restricted](restricted.md)|モジュール、インターフェイス、またはディスパッチ インターフェイスのメンバーを任意に呼び出すことはできませんを指定します。|
|[satype](satype.md)|データ型を指定します、`SAFEARRAY`構造体。|
|[source](source-cpp.md)|コネクション ポイントのソース インターフェイスのコントロールのクラスを指定します。 プロパティまたはメソッドで、`source`属性では、オブジェクトまたはイベントのソースをバリアントにメンバーを返すことを示します。|
|[synchronize](synchronize.md)|ターゲット メソッドへのアクセスを同期します。|
|[vararg](vararg.md)|関数が可変個の引数を実行することを指定します。|

## <a name="see-also"></a>関連項目

[使用法別の属性](attributes-by-usage.md)