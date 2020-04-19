---
title: delete 演算子 (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 3b00bf78d286ba530dee85240236a2a9ea171113
ms.sourcegitcommit: a146b169664c001406a0cccc7fbda1b8d7be5078
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024643"
---
# <a name="delete-operator-c"></a>delete 演算子 (C++)

メモリのブロックを解放します。

## <a name="syntax"></a>構文

> [`::`] `delete` *キャスト式*\
> [`::`] `delete []` *キャスト式*

## <a name="remarks"></a>Remarks

*キャスト式*の引数は、 [new 演算子](../cpp/new-operator-cpp.md)で作成されたオブジェクトに対して以前に割り当てられたメモリブロックへのポインターである必要があります。 **Delete**演算子の結果は**void**型であるため、値を返しません。 例えば:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

**new**で割り当てられていないオブジェクトへのポインターに対して**delete**を使用すると、予測できない結果になります。 ただし、値が0のポインターに対して**delete**を使用することはできます。 このようにプロビジョニングすると、**new**エラーが発生した場合に、新しい操作の結果を削除しても問題はありません。 詳細については、「 [new および delete 演算子](../cpp/new-and-delete-operators.md)」を参照してください。

**New**演算子と**delete**演算子は、配列を含む組み込み型にも使用できます。 が`pointer`配列を参照している場合は、`[]`次の`pointer`前に空の角かっこ () を配置します。

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

オブジェクトに対して**delete**演算子を使用すると、そのメモリの割り当てが解除されます。 オブジェクトを削除した後でポインターを逆参照するプログラムは、予期しない結果になるか、クラッシュする可能性があります。

クラスオブジェクトのメモリの割り当てを解除するために delete を使用すると、オブジェクトのメモリの割り当てが解除される前に、オブジェクトのデストラクターが呼び出されます (オブジェクトにデストラクターがある場合)。 C++

**Delete**演算子のオペランドが変更可能な左辺値の場合、オブジェクトが削除された後、その値は未定義になります。

[/Sdl (追加のセキュリティチェックを有効にする)](/cpp/build/reference/sdl-enable-additional-security-checks)コンパイラオプションが指定されている場合、 **delete**演算子のオペランドは、オブジェクトが削除された後、無効な値に設定されます。

## <a name="using-delete"></a>delete の使用

[Delete 演算子](../cpp/delete-operator-cpp.md)には2つの構文バリアントがあります。1つは単一オブジェクト用で、もう1つはオブジェクトの配列です。 次のコードフラグメントは、両者の違いを示しています。

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

次の2つのケースでは、未定義の結果が生成さ`delete []`れます。オブジェクトに対して array 形式の delete () を使用し、配列で delete の nonarray 形式を使用します。

## <a name="example"></a>例

**Delete**の使用例については、「 [new operator](../cpp/new-operator-cpp.md)」を参照してください。

## <a name="how-delete-works"></a>delete の動作方法

Delete 演算子は、関数**operator delete**を呼び出します。

クラス型 ([クラス](../cpp/class-cpp.md)、[構造体](../cpp/struct-cpp.md)、または[共用体](../cpp/unions.md)) ではないオブジェクトの場合、グローバルな delete 演算子が呼び出されます。 クラス型のオブジェクトの場合、delete 式が単項スコープ解決演算子 (`::`) で始まる場合、割り当て解除関数の名前はグローバルスコープで解決されます。 それ以外の場合、delete 演算子は、メモリ (ポインターが null でない場合) の割り当てを解除する前に、オブジェクトのデストラクターを呼び出します。 delete 演算子は、クラス単位で定義できます。指定のクラスの定義がない場合、グローバル delete 演算子が呼び出されます。 静的な型に仮想デストラクターが含まれるクラス オブジェクトの割り当ての解放に delete 式を使用した場合、deallocation 関数は動的な型のオブジェクトの仮想デストラクターを通じて解決されます。

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)\
[キーワード](../cpp/keywords-cpp.md)\
[new および delete 演算子](../cpp/new-and-delete-operators.md)