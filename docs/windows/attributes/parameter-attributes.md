---
title: パラメーター属性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], parameter attributes
- parameter attributes
ms.assetid: 024c2dd5-49d7-4ced-a17a-c56c1bc485b6
ms.openlocfilehash: e89542027c2187a77c18637432a5b60f47377c10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407446"
---
# <a name="parameter-attributes"></a>パラメーター属性

次の属性は、クラスまたはインターフェイスのメソッドのパラメーターに適用されます。

|属性|説明|
|---------------|-----------------|
|[custom](custom-cpp.md)|独自の属性を定義できます。|
|[defaultvalue](defaultvalue.md)|型指定された省略可能なパラメーターの既定値を指定をできます。|
|[first_is](first-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[iid_is](iid-is.md)|転送する最初の配列要素のインデックスを指定します。|
|[immediatebind](immediatebind.md)|データ バインド オブジェクトのプロパティに対するすべての変更のデータベースに直ちに通知されることを示します。|
|[in](in-cpp.md)|呼び出し元のプロシージャから呼び出されたプロシージャに渡されるパラメーターがあることを示します。|
|[last_is](last-is.md)|転送する最後の配列要素のインデックスを指定します。|
|[lcid](lcid.md)|ロケール識別子を関数に渡すことができます。|
|[length_is](length-is.md)|転送する配列要素の数を指定します。|
|[max_is](max-is.md)|有効な配列のインデックスの最大値を指定します。|
|[optional](optional-cpp.md)|メンバー関数のオプション パラメーターを指定します。|
|[out](out-cpp.md)|呼び出されたプロシージャから呼び出したプロシージャ (サーバーからクライアント) に返されるポインター パラメーターを示します。|
|[range](range-cpp.md)|引数または値を持つが実行時に設定されているフィールドに使用できる値の範囲を指定します。|
|[ref](ref-cpp.md)|参照ポインターを識別します。|
|[retval](retval.md)|メンバーの戻り値を受け取るパラメーターを指定します。|
|[satype](satype.md)|データ型を指定します、`SAFEARRAY`構造体。|
|[size_is](size-is.md)|メモリのサイズがサイズのポインターに割り当てられた、サイズのポインター、および 1 次元または多次元配列へのポインターのサイズを指定します。|
|[unique](unique-cpp.md)|一意のポインターを指定します。|

## <a name="see-also"></a>関連項目

[使用法別の属性](attributes-by-usage.md)