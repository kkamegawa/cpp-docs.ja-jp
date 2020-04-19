---
title: cache_freelist クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: d7840d114acfa0f3daa01c8dfdb6c6114829d93d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689916"
---
# <a name="cache_freelist-class"></a>cache_freelist クラス

1 つのサイズのメモリ ブロックを割り当ておよび割り当て解除する[ブロック アロケーター](../standard-library/allocators-header.md)を定義します。

## <a name="syntax"></a>構文

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Sz*|割り当てられる配列内の要素の数。|
|*Max*|フリー リストの最大サイズを表す max クラスです。 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_variable_size](../standard-library/max-variable-size-class.md) のいずれかにすることができます。|

## <a name="remarks"></a>Remarks

Cache_freelist クラステンプレートは、サイズ*Sz*のメモリブロックの空きリストを保持します。 フリーリストがいっぱいの場合は、 **operator delete**を使用してメモリブロックの割り当てを解除します。 フリーリストが空の場合は、 **operator new**を使用して新しいメモリブロックを割り当てます。 フリーリストの最大サイズは、 *max*パラメーターで渡されるクラス max クラスによって決まります。

各メモリブロックは、使用可能なメモリの*Sz*バイトと、 **operator new**および**operator delete**に必要なデータを保持します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[cache_freelist](#cache_freelist)|`cache_freelist` 型のオブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[allocate](#allocate)|メモリのブロックを割り当てます。|
|[deallocate](#deallocate)|指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="allocate"></a>  cache_freelist::allocate

メモリのブロックを割り当てます。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*count*|割り当てられる配列内の要素の数。|

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

`cache_freelist` 型のオブジェクトを構築します。

```cpp
cache_freelist();
```

### <a name="remarks"></a>Remarks

## <a name="deallocate"></a>  cache_freelist::deallocate

指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|記憶域から割り当てを解除される最初のオブジェクトへのポインター。|
|*count*|記憶域から割り当てを解除されるオブジェクトの数。|

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
