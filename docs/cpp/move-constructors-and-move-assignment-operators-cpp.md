---
title: '方法: 定義の移動コンス トラクターと移動代入演算子 (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: b601c53c01940fe110036d569e0be9d43a123a91
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345023"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>移動コンストラクターと移動代入演算子 (C++)

このトピックでは、記述する方法を説明します、*移動コンス トラクター*と C++ のクラスの移動代入演算子。 移動コンス トラクターには、右辺値をコピーせず、左辺値に移動するオブジェクトによって所有されているリソースができます。 移動セマンティクスの詳細については、次を参照してください。[右辺値参照宣言子: & &](../cpp/rvalue-reference-declarator-amp-amp.md)します。

このセクションは、メモリ バッファーを管理する次の C++ クラス、`MemoryBlock` に基づいています。

```cpp
// MemoryBlock.h
#pragma once
#include <iostream>
#include <algorithm>

class MemoryBlock
{
public:

   // Simple constructor that initializes the resource.
   explicit MemoryBlock(size_t length)
      : _length(length)
      , _data(new int[length])
   {
      std::cout << "In MemoryBlock(size_t). length = "
                << _length << "." << std::endl;
   }

   // Destructor.
   ~MemoryBlock()
   {
      std::cout << "In ~MemoryBlock(). length = "
                << _length << ".";

      if (_data != nullptr)
      {
         std::cout << " Deleting resource.";
         // Delete the resource.
         delete[] _data;
      }

      std::cout << std::endl;
   }

   // Copy constructor.
   MemoryBlock(const MemoryBlock& other)
      : _length(other._length)
      , _data(new int[other._length])
   {
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      std::copy(other._data, other._data + _length, _data);
   }

   // Copy assignment operator.
   MemoryBlock& operator=(const MemoryBlock& other)
   {
      std::cout << "In operator=(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      if (this != &other)
      {
         // Free the existing resource.
         delete[] _data;

         _length = other._length;
         _data = new int[_length];
         std::copy(other._data, other._data + _length, _data);
      }
      return *this;
   }

   // Retrieves the length of the data resource.
   size_t Length() const
   {
      return _length;
   }

private:
   size_t _length; // The length of the resource.
   int* _data; // The resource.
};
```

次の手順では、例の C++ クラスで移動コンストラクターと移動代入演算子を記述する方法を説明します。

### <a name="to-create-a-move-constructor-for-a-c-class"></a>C++ クラスの移動コンストラクターを作成するには

1. 次の例に示すように、パラメーターとしてクラス型への右辺値参照を受け取る、空のコンストラクター メソッドを定義します。

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. 移動コンストラクターで、ソース オブジェクトのクラス データ メンバーを、構築されているオブジェクトに割り当てます。

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. ソース オブジェクトのデータ メンバーを既定値に割り当てます。 これによって、デストラクターがリソース (メモリなど) を繰り返し解放することを防止できます。

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>C++ クラスの移動代入演算子を作成するには

1. 次の例に示すように、パラメーターとしてクラス型への右辺値参照を受け取り、クラス型への参照を返す、空の代入演算子を定義します。

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. 移動代入演算子で、オブジェクトのそれ自身への割り当てが試みられると演算を実行しない条件付きステートメントを追加します。

    ```cpp
    if (this != &other)
    {
    }
    ```

1. 条件付きステートメントでは、割り当てられているオブジェクトからリソース (メモリなど) を解放します。

   次の例は、割り当て先のオブジェクトから `_data` メンバーを解放します。

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   最初の手順の手順 2. と手順 3. を実行し、ソース オブジェクトから構築中のオブジェクトにデータ メンバーを転送します。

    ```cpp
    // Copy the data pointer and its length from the
    // source object.
    _data = other._data;
    _length = other._length;

    // Release the data pointer from the source object so that
    // the destructor does not free the memory multiple times.
    other._data = nullptr;
    other._length = 0;
    ```

1. 次の例に示すように、現在のオブジェクトへの参照を返します。

    ```cpp
    return *this;
    ```

## <a name="example"></a>例

次の例は、`MemoryBlock` クラスの完全な移動コンストラクターと移動代入演算子です。

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "
             << other._length << ". Moving resource." << std::endl;

   // Copy the data pointer and its length from the
   // source object.
   _data = other._data;
   _length = other._length;

   // Release the data pointer from the source object so that
   // the destructor does not free the memory multiple times.
   other._data = nullptr;
   other._length = 0;
}

// Move assignment operator.
MemoryBlock& operator=(MemoryBlock&& other)
{
   std::cout << "In operator=(MemoryBlock&&). length = "
             << other._length << "." << std::endl;

   if (this != &other)
   {
      // Free the existing resource.
      delete[] _data;

      // Copy the data pointer and its length from the
      // source object.
      _data = other._data;
      _length = other._length;

      // Release the data pointer from the source object so that
      // the destructor does not free the memory multiple times.
      other._data = nullptr;
      other._length = 0;
   }
   return *this;
}
```

## <a name="example"></a>例

次の例は、移動セマンティクスがアプリケーションのパフォーマンスをどのように改善するかを示します。 この例では、2 つの要素をベクター オブジェクトに追加し、2 つの既存の要素の間に新しい要素を挿入しています。 `vector`クラスは、移動セマンティクスを効率的にコピーすることではなくベクトルの要素を移動することによって、挿入操作を実行します。

```cpp
// rvalue-references-move-semantics.cpp
// compile with: /EHsc
#include "MemoryBlock.h"
#include <vector>

using namespace std;

int main()
{
   // Create a vector object and add a few elements to it.
   vector<MemoryBlock> v;
   v.push_back(MemoryBlock(25));
   v.push_back(MemoryBlock(75));

   // Insert a new element into the second position of the vector.
   v.insert(v.begin() + 1, MemoryBlock(50));
}
```

この例を実行すると、次の出力が生成されます。

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In operator=(MemoryBlock&&). length = 75.
In operator=(MemoryBlock&&). length = 50.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Visual Studio 2010 では、以前は、この例には、次の出力が生成されます。

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.
In ~MemoryBlock(). length = 75. Deleting resource.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In operator=(const MemoryBlock&). length = 75. Copying resource.
In operator=(const MemoryBlock&). length = 50. Copying resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

移動セマンティクスを使用するこの例のバージョンは、コピー、メモリ割り当て、メモリ解放操作の数が少なくなるため、移動セマンティクスを使用しないバージョンよりも効率的です。

## <a name="robust-programming"></a>信頼性の高いプログラミング

リソース リークを防止するには、移動代入演算子で常にリソース (メモリ、ファイル ハンドル、ソケットなど) を解放します。

リソースの回復不能な破棄を防止するには、移動代入演算子の自己代入を適切に処理します。

クラスに移動コンストラクターと移動代入演算子の両方を指定する場合、移動代入演算子を呼び出すように移動コンストラクターを記述することで、重複するコードを除去できます。 次の例は、移動代入演算子を呼び出す移動コンストラクターの変更済みのバージョンを示します。

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

[Std::move](../standard-library/utility-functions.md#move)関数の rvalue プロパティを保持する、*他*パラメーター。

## <a name="see-also"></a>関連項目

[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std::move](../standard-library/utility-functions.md#move)