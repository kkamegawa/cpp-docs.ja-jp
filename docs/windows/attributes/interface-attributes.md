---
title: インターフェイス属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 8218ccb66c6be9edef5d7de751a73bf4753d069f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409318"
---
# <a name="interface-attributes"></a>インターフェイス属性

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

[使用法別の属性](attributes-by-usage.md)