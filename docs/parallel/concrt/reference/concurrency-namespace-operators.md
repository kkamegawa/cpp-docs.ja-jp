---
title: コンカレンシー名前空間演算子
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 676e1936af317a6ab19959f8fd09b1de06dfaf69
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883773"
---
# <a name="concurrency-namespace-operators"></a>コンカレンシー名前空間演算子

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

## <a name="operator_lor"></a>operator&#124; &#124;演算子

引数として指定されたいずれかのタスクが正常に完了したときに正常に完了するタスクを作成します。

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>パラメーター

*ReturnType*<br/>
返されるタスクの種類。

*lhs*<br/>
結果のタスクにまとめられる最初のタスク。

*rhs*<br/>
結果のタスクにまとめられる 2 番目のタスク。

### <a name="return-value"></a>戻り値

入力タスクのいずれかが正常に完了したときに正常に完了するタスク。 入力したタスクの種類が `T` である場合、この関数の出力は `task<std::vector<T>` になります。 入力したタスクの種類が `void` である場合、出力のタスクも `task<void>` になります。

### <a name="remarks"></a>解説

両方のタスクが取り消された場合、または例外がスローされた場合、返されたタスクは canceled 状態で完了し、例外が発生した場合は、そのタスクで `get()` または `wait()` を呼び出すとスローされます。

## <a name="operator_amp_amp"></a>演算子&amp;&amp; 演算子

引数として指定された両方のタスクが正常に完了したときに正常に完了するタスクを作成します。

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>パラメーター

*ReturnType*<br/>
返されるタスクの種類。

*lhs*<br/>
結果のタスクにまとめられる最初のタスク。

*rhs*<br/>
結果のタスクにまとめられる 2 番目のタスク。

### <a name="return-value"></a>戻り値

入力した両方のタスクが正常に完了したときに正常に完了するタスク。 入力したタスクの種類が `T` である場合、この関数の出力は `task<std::vector<T>>` になります。 入力したタスクの種類が `void` である場合、出力のタスクも `task<void>` になります。

### <a name="remarks"></a>解説

いずれかのタスクが取り消された場合、または例外がスローされた場合、返されたタスクは早期に完了し、取り消された状態になります。また、そのタスクで `get()` または `wait()` を呼び出すと、例外がスローされます。

## <a name="operator_eq_eq"></a>operator = = 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の `concurrent_vector` オブジェクトと等しいかどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の同時実行ベクターが、演算子の右辺の同時実行ベクターと等しい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>解説

2つの同時実行ベクターは、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="operator_neq"></a>operator! = 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の `concurrent_vector` オブジェクトと等しくないかどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

同時実行ベクターが等しくない場合は**true**を返します。同時実行ベクターが等しい場合は**false** 。

### <a name="remarks"></a>解説

2つの同時実行ベクターは、同じ数の要素を持ち、各要素の値が同じである場合に等しくなります。 それ以外の場合は等しくありません。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="operator_lt"></a>operator&lt; 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の `concurrent_vector` オブジェクトより小さいかどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の同時実行ベクターが演算子の右辺の同時実行ベクターより小さい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>解説

この演算子の動作は、`std` 名前空間の `vector` クラスの同等の演算子と同じです。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="operator_lt_eq"></a>operator&lt;= 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の  `concurrent_vector` オブジェクト以下かどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の同時実行ベクターが、演算子の右辺の同時実行ベクター以下である場合は**true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

この演算子の動作は、`std` 名前空間の `vector` クラスの同等の演算子と同じです。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="operator_gt"></a>operator&gt; 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の `concurrent_vector` オブジェクトより大きいかどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の同時実行ベクターが演算子の右辺の同時実行ベクターより大きい場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>解説

この演算子の動作は、`std` 名前空間の `vector` クラスの同等の演算子と同じです。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="operator_gt_eq"></a>operator&gt;= 演算子

演算子の左側の `concurrent_vector` オブジェクトが右側の `concurrent_vector` オブジェクト以上であるかどうかを調べます。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*A1*<br/>
最初の `concurrent_vector` オブジェクトのアロケーター型。

*A2*<br/>
2番目の `concurrent_vector` オブジェクトのアロケーター型。

*_A*<br/>
`concurrent_vector` 型オブジェクト。

*_B*<br/>
`concurrent_vector` 型オブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の同時実行ベクターが演算子の右辺の同時実行ベクター以上の場合、 **true**を返します。それ以外の場合は**false**。

### <a name="remarks"></a>解説

この演算子の動作は、`std` 名前空間の `vector` クラスの同等の演算子と同じです。

このメソッドは、同時実行ベクター `_A` または `_B`のいずれかを変更する可能性のある他のメソッドに関して、同時実行セーフではありません。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
