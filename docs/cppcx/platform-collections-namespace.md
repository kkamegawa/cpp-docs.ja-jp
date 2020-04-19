---
title: Platform::Collections 名前空間
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: 025c25d6c01ab9a28c68574cc2a13e09dbf28388
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161746"
---
# <a name="platformcollections-namespace"></a>Platform::Collections 名前空間

Platform::collections 名前空間が含まれています、 `Map`、 `MapView`、 `Vector`、および`VectorView`クラス。 これらのクラスは、 [Windows::Foundation::Collections](/uwp/api/Windows.Foundation.Collections) 名前空間に定義されている、対応するインターフェイスの具象実装です。 具体的なコレクション型は、(Javascript または C# で書かれたプログラムが C++ コンポーネントを呼び出すなど) ABI を越えて移植することはできませんが、対応するインターフェイスの型に暗黙的に変換できます。 たとえば、コレクションを設定して返すパブリック メソッドを実装する場合は、 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) を使用して内部的にコレクションを実装し、 [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) を戻り値の型として使用します。 詳細については、次を参照してください。[コレクション](../cppcx/collections-c-cx.md)と[C++ での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)です。

Platform::Collections::Vector は [std::vector](../standard-library/vector-class.md) から構築でき、 [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) は [std::map](../standard-library/map-class.md)から構築できます。

さらに、platform::collections 名前空間は挿入し、入力反復子のサポートを提供し、`Vector`と`VectorView`反復子。

含める必要があります (`#include`) platform::collections 名前空間の型の使用には、collection.h ヘッダー。

## <a name="syntax"></a>構文

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>メンバー

この名前空間には、次のメンバーが含まれます。

|名前|説明|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator クラス](../cppcx/platform-collections-backinsertiterator-class.md)|コレクションの末尾に要素を挿入する反復子を表します。|
|[Platform::Collections::InputIterator クラス](../cppcx/platform-collections-inputiterator-class.md)|コレクションの先頭に要素を挿入する反復子を表します。|
|[Platform::Collections::Map クラス](../cppcx/platform-collections-map-class.md)|キーによりアクセスされるキーと値のペアの変更可能なコレクションを表します。 [std::map](../standard-library/map-class.md)に似ています。|
|[Platform::Collections::MapView クラス](../cppcx/platform-collections-mapview-class.md)|キーによりアクセスされるキーと値のペアの読み取り専用のコレクションを表します。|
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|要素の変更可能なシーケンスを表します。 [std::vector](../standard-library/vector-class.md)に似ています。|
|[Platform::Collections::VectorIterator クラス](../cppcx/platform-collections-vectoriterator-class.md)|`Vector` コレクションを走査する反復子を表します。|
|[Platform::Collections::VectorView クラス](../cppcx/platform-collections-vectorview-class.md)|要素の読み取り専用のシーケンスを表します。|
|[Platform::Collections::VectorViewIterator クラス](../cppcx/platform-collections-vectorviewiterator-class.md)|`VectorView` コレクションを走査する反復子を表します。|

## <a name="inheritance-hierarchy"></a>継承階層

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>必要条件

**メタデータ:** platform.winmd

**名前空間:** Platform::Collections

**コンパイラ オプション:** /ZW

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](../cppcx/platform-namespace-c-cx.md)
