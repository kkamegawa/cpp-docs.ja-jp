---
title: ポインター (C++)
ms.date: 11/19/2019
description: Microsoft C++における生のポインターとスマートポインターについて説明します。
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246415"
---
# <a name="pointers-c"></a>ポインター (C++)

ポインターは、オブジェクトのメモリアドレスを格納する変数です。 ポインターは、次の3つのC++主な目的で、C との両方で広く使用されています。

- ヒープに新しいオブジェクトを割り当てるには、
- 関数を他の関数に渡すには
- 配列またはその他のデータ構造体の要素を反復処理する場合は。

C スタイルのプログラミングでは、これらすべてのシナリオに*生のポインター*が使用されます。 しかし、生のポインターは、多くの重大なプログラミングエラーの原因になります。 そのため、パフォーマンスが大幅に向上し、オブジェクトの削除を*担当するポインター*がどのポインターであるかについて、あいまいさがないことを除いて、使用することはお勧めしません。 モダンC++には、オブジェクトを割り当てるための*スマートポインター* 、データ構造を走査する*反復子*、および関数を渡す*ラムダ式*が用意されています。 生のポインターではなく、これらの言語およびライブラリ機能を使用することにより、プログラムの安全性とデバッグが容易になり、理解と保守が簡単になります。 詳細については、「[スマートポインター](smart-pointers-modern-cpp.md)、[反復子](../standard-library/iterators.md)、および[ラムダ式](lambda-expressions-in-cpp.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

- [生のポインター](raw-pointers.md)
- [Const ポインターと volatile ポインター](const-and-volatile-pointers.md)
- [new 演算子と delete 演算子](new-and-delete-operators.md)
- [スマートポインター](smart-pointers-modern-cpp.md)
- [方法: unique_ptr インスタンスを作成して使用する](how-to-create-and-use-unique-ptr-instances.md)
- [方法: shared_ptr インスタンスを作成して使用する](how-to-create-and-use-shared-ptr-instances.md)
- [方法: weak_ptr インスタンスを作成して使用する](how-to-create-and-use-weak-ptr-instances.md)
- [方法: CComPtr インスタンスと CComQIPtr インスタンスを作成して使用する](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>参照

[反復子](../standard-library/iterators.md)</br>
[ラムダ式](lambda-expressions-in-cpp.md)
