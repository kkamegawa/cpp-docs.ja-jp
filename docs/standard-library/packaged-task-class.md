---
title: packaged_task クラス
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: 5bb04b84b723f239c338c02befa8cd3468cec3f2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450074"
---
# <a name="packagedtask-class"></a>packaged_task クラス

呼び出しラッパーであり、呼び出しシグネチャが `Ty(ArgTypes...)` である*非同期プロバイダー*を記述します。 その*関連付けられた非同期状態*には、可能性がある結果に加えて呼び出し可能オブジェクトのコピーが保持されます。

## <a name="syntax"></a>構文

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[packaged_task](#packaged_task)|`packaged_task` オブジェクトを構築します。|
|[packaged_task::~packaged_task デストラクター](#dtorpackaged_task_destructor)|`packaged_task` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[get_future](#get_future)|同じ関連付けられた非同期状態の [future](../standard-library/future-class.md) オブジェクトを返します。|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|関連付けられた非同期状態に格納された呼び出し可能オブジェクトを呼び出し、戻り値をアトミックに格納します。|
|[reset](#reset)|関連付けられた非同期状態を置き換えます。|
|[swap](#swap)|関連付けられた非同期状態を、指定したオブジェクトのものと交換します。|
|[valid](#valid)|オブジェクトが関連付けられた非同期状態であるかどうかを指定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|関連付けられた非同期状態を、指定されたオブジェクトから転送します。|
|[packaged_task::operator()](#op_call)|関連付けられた非同期状態に格納された呼び出し可能オブジェクトを呼び出し、戻り値をアトミックに格納し、状態を *ready* に設定します。|
|[packaged_task::operator bool](#op_bool)|オブジェクトが関連付けられた非同期状態であるかどうかを指定します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<今後の >

**名前空間:** std

## <a name="get_future"></a>  packaged_task::get_future

同じ*関連付けられた非同期状態*の `future<Ty>` 型のオブジェクトを返します。

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Remarks

`packaged_task` オブジェクトが関連付けられた非同期状態ではない場合、このメソッドはエラー コード `no_state` で [future_error](../standard-library/future-error-class.md) をスローします。

このメソッドが同じ関連付けられた非同期状態の `packaged_task` オブジェクトに対して既に呼び出されている場合、このメソッドはエラー コード `future_already_retrieved` で `future_error` をスローします。

## <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit

*関連付けられた非同期状態*に格納された呼び出し可能オブジェクトを呼び出し、戻り値をアトミックに格納します。

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Remarks

`packaged_task` オブジェクトが関連付けられた非同期状態ではない場合、このメソッドはエラー コード `no_state` で [future_error](../standard-library/future-error-class.md) をスローします。

このメソッドまたは [make_ready_at_thread_exit](#make_ready_at_thread_exit) が同じ関連付けられた非同期状態の `packaged_task` オブジェクトに対して既に呼び出されている場合、このメソッドはエラー コード `promise_already_satisfied` で `future_error` をスローします。

それ以外の場合、この演算子は `INVOKE(fn, args..., Ty)` を呼び出します。ここで、*fn* は関連付けられた非同期状態に格納された呼び出し可能オブジェクトです。 すべての戻り値は、関連付けられた非同期状態の返された結果としてアトミックに格納されます。

[packaged_task::operator()](#op_call) とは対照的に、呼び出し元のスレッドのスレッド ローカルのオブジェクトがすべて破棄されるまでは、関連付けられた非同期状態は `ready` に設定されません。 通常、関連付けられた非同期状態でブロックされたスレッドは、呼び出し元のスレッドが終了するまでブロック解除されません。

## <a name="op_eq"></a>  packaged_task::operator=

*関連付けられた非同期状態*を、指定されたオブジェクトから転送します。

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
`packaged_task` オブジェクト。

### <a name="return-value"></a>戻り値

`*this`

### <a name="remarks"></a>Remarks

操作の後、*右側*には関連付けられた非同期状態がありません。

## <a name="op_call"></a>  packaged_task::operator()

*関連付けられた非同期状態*に格納された呼び出し可能オブジェクトを呼び出し、戻り値をアトミックに格納し、状態を *ready* に設定します。

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Remarks

`packaged_task` オブジェクトが関連付けられた非同期状態ではない場合、このメソッドはエラー コード `no_state` で [future_error](../standard-library/future-error-class.md) をスローします。

このメソッドまたは [make_ready_at_thread_exit](#make_ready_at_thread_exit) が同じ関連付けられた非同期状態の `packaged_task` オブジェクトに対して既に呼び出されている場合、このメソッドはエラー コード `promise_already_satisfied` で `future_error` をスローします。

それ以外の場合、この演算子は `INVOKE(fn, args..., Ty)` を呼び出します。ここで、*fn* は関連付けられた非同期状態に格納された呼び出し可能オブジェクトです。 すべての戻り値は、関連付けられた非同期状態の返された結果としてアトミックに格納され、状態が ready に設定されます。 その結果、関連付けられた非同期状態でブロックされているすべてのスレッドがブロック解除されます。

## <a name="op_bool"></a>  packaged_task::operator bool

オブジェクトが `associated asynchronous state` であるかどうかを指定します。

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられた非同期状態がある場合は**true** 。それ以外の場合は**false**。

## <a name="packaged_task"></a>  packaged_task::packaged_task コンストラクター

`packaged_task` オブジェクトを構築します。

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>パラメーター

*そうです*\
`packaged_task` オブジェクト。

*割り当て*\
メモリ割り当て。 詳細については、「[\<allocators>](../standard-library/allocators-header.md)」を参照してください。

*1億*\
関数オブジェクトを指定します。

### <a name="remarks"></a>Remarks

1 つ目のコンストラクターは、*関連付けられた非同期状態*がない `packaged_task` オブジェクトを構築します。

2番目のコンストラクター `packaged_task`は、オブジェクトを構築し、関連付けられた非同期状態を*右*から転送します。 操作の後、*右側*には関連付けられた非同期状態がありません。

3番目のコンストラクター `packaged_task`は、関連付けられた非同期状態に*fn*のコピーが格納されているオブジェクトを構築します。

4番目のコンストラクター `packaged_task`は、関連付けられた非同期状態に*fn*というコピーが格納`alloc`されているオブジェクトを構築し、メモリ割り当てにを使用します。

## <a name="dtorpackaged_task_destructor"></a>  packaged_task::~packaged_task デストラクター

`packaged_task` オブジェクトを破棄します。

```cpp
~packaged_task();
```

### <a name="remarks"></a>Remarks

*関連付けられた非同期状態*が*準備完了*ではない場合、デストラクターは、関連付けられた非同期状態の結果としてエラー コード `broken_promise` で [future_error](../standard-library/future-error-class.md) 例外を格納し、関連付けられた非同期状態でブロックされているすべてのスレッドがブロック解除されます。

## <a name="reset"></a>  packaged_task::reset

新しい*関連付けられた非同期状態*を使用して、既存の関連付けられた非同期状態を置き換えます。

```cpp
void reset();
```

### <a name="remarks"></a>Remarks

実際には、このメソッドは `*this = packaged_task(move(fn))` を実行します。ここで、*fn* は、このオブジェクトの関連付けられた非同期状態に格納された関数オブジェクトです。 そのため、オブジェクトの状態が削除され、[get_future](#get_future)、[operator()](#op_call)、および [make_ready_at_thread_exit](#make_ready_at_thread_exit) を新しく構築されたオブジェクトでのように呼び出すことができます。

## <a name="swap"></a>  packaged_task::swap

関連付けられた非同期状態を、指定したオブジェクトのものと交換します。

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
`packaged_task` オブジェクト。

## <a name="valid"></a>  packaged_task::valid

オブジェクトが `associated asynchronous state` であるかどうかを指定します。

```cpp
bool valid() const;
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられた非同期状態がある場合は**true** 。それ以外の場合は**false**。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
