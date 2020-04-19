---
title: スタンドアロン属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 7dd1f35add3b23dbd81e32a1600481eec79fe7d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407264"
---
# <a name="stand-alone-attributes"></a>スタンドアロン属性

スタンドアロン属性は C++ キーワードについては動作しませんが、行のコードのようにします。 スタンドアロン属性ステートメントには、行の末尾にセミコロンが必要です。

## <a name="stand-alone-attribute-list"></a>スタンドアロン属性の一覧

|属性|説明|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|生成されたヘッダー ファイルに、引用符なしの指定した文字列を出力します。|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[db_command](db-command.md)|OLE DB コマンドを作成します。|
|[emitidl](emitidl.md)|後続のすべての IDL 属性が処理され、生成された .idl ファイル内に配置するかどうかを判断します。|
|[idl_module](idl-module.md)|DLL エントリ ポイントを指定します。|
|[idl_quote](idl-quote.md)|Visual C の現在のバージョンでサポートされていない IDL コンストラクトを使用することができ、生成された .idl ファイルに渡すことがあります。|
|[import](import.md)|メインの .idl ファイルから参照する定義を含む別の .idl、.odl ファイル、または .h ファイルを指定します。|
|[importidl](importidl.md)|生成された .idl ファイルに指定された .idl ファイルを挿入します。|
|[importlib](importlib.md)|既に他のタイプ ライブラリでコンパイル済みの型を、作成中のタイプ ライブラリで使用できるようにします。|
|[include](include-cpp.md)|生成された .idl ファイルに含まれる 1 つまたは複数のヘッダー ファイルを指定します。|
|[includelib](includelib-cpp.md)|生成された .idl ファイルに含まれる、.idl ファイルまたは .h ファイル。|
|[library_block](library-block.md)|.Idl ファイルのライブラリ ブロック内で構成要素を配置します。|
|[module](module-cpp.md)|.idl ファイルのライブラリ ブロックを定義します。|
|[no_injected_text](no-injected-text.md)|コンパイラがコードの属性を使用した結果として挿入するを防ぎます。|
|[pragma](pragma.md)|生成された .idl ファイルに、引用符なしの指定した文字列を出力します。|

## <a name="see-also"></a>関連項目

[使用法別の属性](attributes-by-usage.md)