---
title: 明示的なインスタンス化
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 45661653b4b8f1a4f94ece1c53aa86f4a431700b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392207"
---
# <a name="explicit-instantiation"></a>明示的なインスタンス化

明示的なインスタンス化によって、テンプレート化されたクラスまたは関数をコードで実際に使用することなく、そのインスタンスを作成できます。 配布用のテンプレートを使用するライブラリ (.lib) ファイルを作成する場合は、この方法が便利です。そのため、インスタンス化されないテンプレート定義はオブジェクト (.obj) ファイルに格納されません。

このコードは明示的にインスタンス化`MyStack`の**int**変数と 6 つの項目。

```cpp
template class MyStack<int, 6>;
```

このステートメントは、オブジェクトのためのストレージを予約しないで `MyStack` のインスタンス化を作成します。 コードはすべてのメンバーに対して生成されます。

次の行はコンストラクター メンバー関数のみを明示的にインスタンス化します。

```cpp
template MyStack<int, 6>::MyStack( void );
```

例で示すように、再宣言する特定の型引数を使用して、関数テンプレートをインスタンス化することが明示的に[関数テンプレートのインスタンス化](../cpp/function-template-instantiation.md)します。

使用することができます、 **extern**メンバーの自動インスタンス化されないようにするキーワード。 例:

```cpp
extern template class MyStack<int, 6>;
```

同様に、外部のインスタンス化されていないメンバーとして特定のメンバーを次のようにマークできます。

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

使用することができます、 **extern**キーワードをコンパイラがオブジェクトの 1 つ以上のモジュールで、同じインスタンス化コードを生成することを防止します。 関数が呼び出される場合には、少なくとも 1 つのリンクされたモジュールで指定した明示的なテンプレート パラメーターを使用して、テンプレート関数をインスタンス化する必要があります。そのようにインスタンス化しないと、プログラムのビルド時にリンカー エラーが発生します。

> [!NOTE]
>  **Extern**特殊化のキーワードはクラスの本体の外部で定義されているメンバー関数にのみ適用されます。 クラス宣言内で定義されている関数はインライン関数と見なされ、常にインスタンス化されます。

## <a name="see-also"></a>関連項目

[関数テンプレート](../cpp/function-templates.md)