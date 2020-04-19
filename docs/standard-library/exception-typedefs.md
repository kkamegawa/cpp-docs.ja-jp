---
title: '&lt;exception&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
ms.openlocfilehash: aba17b7bf052b6974bf849f60ff895b8e84a1092
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501958"
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; typedefs

## <a name="exception_ptr"></a>  exception_ptr

例外へのポインターを表す型。

```cpp
typedef unspecified exception_ptr;
```

### <a name="remarks"></a>Remarks

`exception_ptr` 型を実装するために使用される未指定の内部クラス。

現在の例外またはユーザーが指定した例外のインスタンスを参照するには、`exception_ptr` オブジェクトを使用します。 Microsoft の実装では、例外は [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) 構造体によって表されます。 各 `exception_ptr` オブジェクトには、例外を表す `EXCEPTION_RECORD` 構造体のコピーを指す例外参照フィールドが含まれています。

`exception_ptr` 変数を宣言する場合、変数は例外に関連付けられません。 つまり、例外参照フィールドが NULL です。 このような `exception_ptr` オブジェクトは、*null exception_ptr* と呼ばれます。

例外を `current_exception` オブジェクトに割り当てるには、`make_exception_ptr` または `exception_ptr` 関数を使用します。 `exception_ptr` 変数に例外を割り当てた場合、変数の例外参照フィールドは例外のコピーを指します。 例外をコピーするためのメモリが不足している場合、例外参照フィールドは、[std::bad_alloc](../standard-library/bad-alloc-class.md) 例外のコピーを指し示します。 または`current_exception` `make_exception_ptr`関数が他の理由で例外をコピーできない場合`terminate` 、関数は CRT 関数を呼び出して現在のプロセスを終了します。

名前とは異なり、`exception_ptr` オブジェクト自体はポインターではありません。 ポインターのセマンティクスに従わず、ポインターのメンバー アクセス (`->`) 演算子または間接 (*) 演算子で使用することはできません。 `exception_ptr` オブジェクトには、パブリック データ メンバーまたはメンバー関数がありません。

**比較:**

等値演算子 (`==`) と不等値演算子 (`!=`) を使用して、2 種類の `exception_ptr` オブジェクトを比較できます。 演算子は、例外を表す `EXCEPTION_RECORD` 構造体のバイナリ値 (ビット パターン) は比較しません。 代わりに、演算子は `exception_ptr` オブジェクトの例外参照フィールドのアドレスを比較します。 その結果、null `exception_ptr` と NULL 値を比較すると、等しいと評価されます。

## <a name="terminate_handler"></a>terminate_handler

この型は、`terminate_handler` として使用するのに適した関数へのポインターを表します。

```cpp
typedef void (*terminate_handler)();
```

### <a name="remarks"></a>Remarks

この型は、終了ハンドラーとして使用するのに適した関数へのポインターを表します。

### <a name="example"></a>例

`terminate_handler` の使用例については、「[set_terminate](../standard-library/exception-functions.md#set_terminate)」を参照してください。

## <a name="unexpected_handler"></a>unexpected_handler

この型は、`unexpected_handler` として使用するのに適した関数へのポインターを表します。

```cpp
typedef void (*unexpected_handler)();
```

### <a name="example"></a>例

`unexpected_handler` の使用例については、「[set_unexpected](../standard-library/exception-functions.md#set_unexpected)」を参照してください。
