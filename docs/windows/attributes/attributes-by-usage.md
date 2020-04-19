---
title: 使用法別の属性
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: f6567a7866516c09bca03fa9f3d3aa5aa997b6b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148454"
---
# <a name="attributes-by-usage"></a>使用法別の属性

このトピックでは、C++ 言語要素を適用するに従って属性を使用します。

場合は、属性のスコープではない要素の直前に、属性、属性ブロックはコメントとして扱われます。

|属性|説明|
|---------------|-----------------|
|[モジュール属性](module-attributes.md)|適用されます、[モジュール](module-cpp.md)属性。|
|[インターフェイス属性](interface-attributes.md)|適用されます、 [_ _interface](../../cpp/interface.md) C++キーワード。|
|[クラス属性](class-attributes.md)|C++ のキーワードを適用します。|
|[メソッド属性](method-attributes.md)|クラス、コクラスまたはインターフェイスのメソッドに適用されます。|
|[パラメーター属性](parameter-attributes.md)|クラスまたはインターフェイスのメソッドのパラメーターに適用されます。|
|[データ メンバー属性](data-member-attributes.md)|クラス、コクラスまたはインターフェイス内のデータ メンバーに適用されます。|
|[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)|C++ のキーワードを適用します。|
|[配列属性](array-attributes.md)|アレイに適用されるまたは`SAFEARRAY`s。|
|[スタンドアロン属性](stand-alone-attributes.md)|コード行のような動作をしますが、C++ のキーワードについては動作しません。 スタンドアロン属性ステートメントには、行の末尾にセミコロンが必要です。|
|[カスタム属性](custom-attributes-cpp.md)|メタデータを拡張できます。|

## <a name="module-attributes"></a>モジュール属性
次の属性にのみ適用、[モジュール](module-cpp.md)属性。

|属性|説明|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|使用してドキュメントの文字列の検索 (ローカライズ) を実行する DLL の名前を指定します。|

## <a name="interface-attributes"></a>インターフェイス属性

次の属性を適用する、[インターフェイス (または _ _interface)](../../cpp/interface.md) C++キーワード。

|属性|説明|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|同期および非同期の両方のバージョンの COM インターフェイスを定義する、MIDL コンパイラに指示する UUID を指定します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[dispinterface](dispinterface.md)|ディスパッチ インターフェイスとしてインターフェイスを .idl ファイルに配置します。|
|[dual](dual.md)|.Idl ファイルにデュアル インターフェイスとしてインターフェイスを配置します。|
|[export](export.md)|.Idl ファイルに配置するデータ構造をによりします。|
|[helpcontext](helpcontext.md)|ユーザーがヘルプ ファイル内のこの要素についての情報を表示できるようにコンテキスト ID を指定します。|
|[helpfile](helpfile.md)|タイプ ライブラリのヘルプ ファイルの名前を設定します。|
|[helpstring](helpstring.md)|適用先となる要素を記述するために使用される文字列を指定します。|
|[helpstringcontext](helpstringcontext.md)|.Hlp または .chm ファイルをヘルプ トピックの ID を指定します。|
|[helpstringdll](helpstringdll.md)|使用してドキュメントの文字列の検索 (ローカライズ) を実行する DLL の名前を指定します。|
|[hidden](hidden.md)|項目が存在しますが、ユーザー指向ブラウザーで表示する必要がありますされませんを示します。|
|[library_block](library-block.md)|.Idl ファイルのライブラリ ブロック内で構成要素を配置します。|
|[local](local-cpp.md)|インターフェイスのヘッダーで使用する場合は、ヘッダー ジェネレーターとして、MIDL コンパイラを使用することができます。 個々 の関数で使用する場合は、スタブが生成されたないローカル プロシージャを指定します。|
|[nonextensible](nonextensible.md)|指定します、`IDispatch`実装にはプロパティのみが含まれていて、メソッドは、インターフェイスの説明に記載して、実行時にメンバーを追加して拡張することはできません。 この属性でのみ有効です、[デュアル](dual.md)インターフェイス。|
|[odl](odl.md)|オブジェクト記述言語 (ODL) インターフェイスとしてインターフェイスを識別します。|
|[object](object-cpp.md)|カスタム インターフェイスを識別します。|
|[oleautomation](oleautomation.md)|インターフェイスが Automation と互換性があることを示します。|
|[pointer_default](pointer-default.md)|パラメーター リストで表示される最上位レベルのポインターを除くすべてのポインターの既定のポインターの属性を指定します。|
|[ptr](ptr.md)|完全なポインターとしてのポインターを指定します。|
|[restricted](restricted.md)|ライブラリのメンバーを任意に呼び出すことはできませんを指定します。|
|[uuid](uuid-cpp-attributes.md)|ライブラリの一意の ID を提供します。|

インターフェイスを定義するため、これらの規則に従う必要があります。

- 既定の呼び出し規約は[_ _stdcall](../../cpp/stdcall.md)します。

- いずれかを指定しない場合、GUID が指定されます。

- オーバー ロードされたメソッドは許可されません。

指定しない場合、 [uuid](uuid-cpp-attributes.md)属性し、同じインターフェイスの名前を使用して、別の属性のプロジェクトで、同じ GUID が生成されます。

## <a name="see-also"></a>関連項目

[COM および .NET の C++ の属性](cpp-attributes-com-net.md)<br/>
[グループ別の属性](attributes-by-group.md)<br/>
[属性リファレンス (アルファベット順)](attributes-alphabetical-reference.md)