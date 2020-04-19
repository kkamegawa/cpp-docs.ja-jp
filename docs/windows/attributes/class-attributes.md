---
title: クラス属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: d0913d09c51734f5255271c0d06e639810e0cb58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148420"
---
# <a name="class-attributes"></a>クラス属性

次の属性を適用する、[クラス](../../cpp/class-cpp.md)C++ のキーワード。

|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|クラスは、集計をサポートしていることを示します。|
|[aggregates](aggregates.md)|コントロールがターゲット クラスを集約することを示します。|
|[appobject](appobject.md)|完全な .exe アプリケーションに関連付けられ、関数と、コクラスのプロパティがグローバルに使用できるこのタイプ ライブラリを示しますアプリケーション オブジェクトとしてコクラスを識別します。|
|[case](case-cpp.md)|使用される、 [switch_type](switch-type.md)共用体の属性。|
|[coclass](coclass.md)|ActiveX コントロールを作成します。|
|[com_interface_entry](com-interface-entry-cpp.md)|COM マップには、インターフェイスのエントリを追加します。|
|[control](control.md)|コントロールに、ユーザー定義型を指定します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[db_command](db-command.md)|OLE DB コマンドを作成します。|
|[db_param](db-param.md)|入力または出力パラメーターを使用して、指定したメンバー変数を関連付けるし、変数を区切ります。|
|[db_source](db-source.md)|データ ソースへの接続を作成します。|
|[db_table](db-table.md)|OLE DB、テーブルを開きます。|
|[default](default-cpp.md)|コクラス内で定義されるカスタムまたはディスパッチ インターフェイスが既定のプログラミング インターフェイスを表すことを示します。|
|[defaultvtable](defaultvtable.md)|コントロールの既定の vtable インターフェイスとしてインターフェイスを定義します。|
|[event_receiver](event-receiver.md)|イベント レシーバーを作成します。|
|[event_source](event-source.md)|イベント ソースを作成します。|
|[helpcontext](helpcontext.md)|ユーザーには、この要素に関する情報を表示できるようにコンテキスト ID を指定します、**ヘルプ**ファイル。|
|[helpfile](helpfile.md)|タイプ ライブラリのヘルプ ファイルの名前を設定します。|
|[helpstringcontext](helpstringcontext.md)|.Hlp または .chm ファイルをヘルプ トピックの ID を指定します。|
|[helpstring](helpstring.md)|適用先となる要素を記述するために使用される文字列を指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[implements](implements-cpp.md)|IDL コクラスのメンバーであるが強制されているディスパッチ インターフェイスを指定します。|
|[implements_category](implements-category.md)|クラスの実装されたコンポーネントのカテゴリを指定します。|
|[module](module-cpp.md)|.idl ファイルのライブラリ ブロックを定義します。|
|[noncreatable](noncreatable.md)|単独でインスタンス化できないオブジェクトを定義します。|
|[progid](progid.md)|コントロールの ProgID を定義します。|
|[registration_script](registration-script.md)|指定した登録スクリプトを実行します。|
|[requestedit](requestedit.md)|`OnRequestEdit` 通知がプロパティでサポートされることを示します。|
|[source](source-cpp.md)|コネクション ポイントのソース インターフェイスのコントロールのクラスを指定します。 プロパティまたはメソッドで、`source`属性は、メンバーがオブジェクトを返すことを示しますまたは`VARIANT`イベントのソースは。|
|[support_error_info](support-error-info.md)|ターゲット オブジェクトのエラー報告をサポートしています。|
|[threading](threading-cpp.md)|コントロールのスレッド モデルを指定します。|
|[uuid](uuid-cpp-attributes.md)|クラスまたはインターフェイスの一意の ID を指定します。|
|[version](version-cpp.md)|クラスの複数のバージョン間で特定のバージョンを識別します。|
|[vi_progid](vi-progid.md)|ProgID のバージョンに依存しない形式を指定します。|

## <a name="see-also"></a>関連項目

[使用法別の属性](attributes-by-usage.md)