---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 515318cda2155db81406a5c23cb64e46e79c4e19
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448421"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

標準ヘッダー \<mutex> をインクルードすることにより、クラス `mutex`、`recursive_mutex`、`timed_mutex`、`recursive_timed_mutex`、テンプレート `lock_guard` および `unique_lock`、相互排他コード領域を定義するためサポートしている型と関数を定義します。

> [!WARNING]
> Visual Studio 2015 以降では、 C++標準ライブラリの同期の種類は windows 同期プリミティブに基づいており、concrt を使用しなくなりました (ターゲットプラットフォームが windows XP の場合を除く)。 \<mutex> で定義されている型は、ConcRT 型または関数には使用しないでください。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ミューテックス >

**名前空間:** std

## <a name="remarks"></a>Remarks

> [!NOTE]
> **/Clr**を使用してコンパイルされたコードでは、このヘッダーはブロックされます。

クラス `mutex` と`recursive_mutex` は *mutex 型*です。 mutex 型には、既定のコンストラクターとデストラクターがあり、例外をスローしません。 これらのオブジェクトには、同じオブジェクトをロックしようとしている複数のスレッドがある場合に相互排他するためのメソッドがあります。 具体的には、mutex 型にはメソッド `lock`、`try_lock`、および`unlock` が含まれます。

- `lock` メソッドは、スレッドがミューテックスの所有権を得るまでそのスレッドの呼び出しをブロックします。 その戻り値は無視されます。

- `try_lock` メソッドは、ミューテックスをブロックせずに所有権を取得しようとします。 戻り値の型は**ブール**型に変換でき、メソッドが所有権を取得した場合は**true**になりますが、それ以外の場合は**false**になります。

- `unlock` メソッドは、呼び出し元のスレッドからミューテックスの所有権を解放します。

型の引数として mutex 型を使用すると、テンプレート `lock_guard` と `unique_lock` をインスタンス化できます。 これらの型のオブジェクトを `Lock` 引数として使用すると、テンプレート [condition_variable_any](../standard-library/condition-variable-any-class.md) でメンバー関数を待機できます。

*timed mutex type* は mutex 型の要件を満たします。 また、1つの引数`try_lock_for`を`try_lock_until`使用して呼び出し可能で、**ブール**型に変換できる型を返す必要があるメソッドとメソッドがあります。 timed mutex 型では、追加の引数を使用してこれらの関数を定義できます (追加の引数すべてに既定値があることが条件)。

- `try_lock_for` メソッドは、型が [chrono::duration](../standard-library/duration-class.md) でインスタンス化されている 1 つの引数 `Rel_time` を使用して呼び出し可能である必要があります。 メソッドはミューテックスの所有権を取得しようとしますが、取得できたかどうかに関係なく、`Rel_time` で指定された時間内に値が返されます。 メソッドが所有権を取得した場合、戻り値は**true**に変換されます。それ以外の場合、戻り値は**false**に変換されます。

- `try_lock_until` メソッドは、型が [chrono::time_point](../standard-library/time-point-class.md) でインスタンス化されている引数 `Abs_time` を使用して呼び出し可能である必要があります。 メソッドはミューテックスの所有権を取得しようとしますが、取得できたかどうかに関係なく、`Abs_time` で指定された時間内に値が返されます。 メソッドが所有権を取得した場合、戻り値は**true**に変換されます。それ以外の場合、戻り値は**false**に変換されます。

mutex 型は *lockable 型*とも呼ばれます。 メンバー関数 `try_lock` が提供されない場合は、*basic lockable 型*になります。 timed mutex 型は *timed lockable 型*とも呼ばれます。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|||
|-|-|
|[lock_guard クラス](../standard-library/lock-guard-class.md)|オブジェクトを作成し、そのデストラクタ―が `mutex` のロックを解除するためにインスタンス化できるテンプレートを表します。|
|[mutex クラス (C++ 標準ライブラリ)](../standard-library/mutex-class-stl.md)|mutex 型を表します。 この型のオブジェクトを使用して、プログラム内で相互排他を適用します。|
|[recursive_mutex クラス](../standard-library/recursive-mutex-class.md)|mutex 型を表します。 `mutex` クラスとは異なり、既にロックされているオブジェクトのロック メソッドを呼び出す動作は詳細に定義されています。|
|[recursive_timed_mutex クラス](../standard-library/recursive-timed-mutex-class.md)|timed mutex 型を表します。 この型のオブジェクトを使用して、プログラム内で時間制限ブロックのある相互排他を適用します。 `timed_mutex` 型のオブジェクトとは異なり、`recursive_timed_mutex` オブジェクトにロック メソッドを呼び出すことによる影響は詳細に定義されています。|
|[scoped_lock クラス](../standard-library/scoped-lock-class.md)||
|[timed_mutex クラス](../standard-library/timed-mutex-class.md)|timed mutex 型を表します。 この型のオブジェクトを使用して、プログラム内で時間制限ブロックのある相互排他を適用します。|
|[unique_lock クラス](../standard-library/unique-lock-class.md)|`mutex` のロックとロック解除を管理するオブジェクトを作成するためにインスタンス化できるテンプレートを表します。|

### <a name="functions"></a>関数

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|指定された呼び出し可能オブジェクトが、実行中に 1 回だけ呼び出されるメカニズムを提供します。|
|[lock](../standard-library/mutex-functions.md#lock)|デッドロックなしですべての引数をロックしようとします。|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>構造体

|||
|-|-|
|[adopt_lock_t 構造体](../standard-library/adopt-lock-t-structure.md)|`adopt_lock` の定義に使用する型を表します。|
|[defer_lock_t 構造体](../standard-library/defer-lock-t-structure.md)|`unique_lock` のオーバーロード コンストラクターの 1 つを選択するために使用される、`defer_lock` オブジェクトを定義する型を表します。|
|[once_flag 構造体](../standard-library/once-flag-structure.md)|実行の複数のスレッドが存在する場合で`call_once`も、初期化コードが1回だけ呼び出されるようにするために、テンプレート関数で使用される**構造体**を表します。|
|[try_to_lock_t 構造体](../standard-library/try-to-lock-t-structure.md)|オブジェクトを`try_to_lock`定義し、の`unique_lock`オーバーロードされたコンストラクターの1つを選択するために使用される**構造体**を表します。|

### <a name="variables"></a>変数

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|`lock_guard` と `unique_lock` のコンストラクターに渡されるオブジェクを表し、同じコンストラクターに渡されるミューテックス オブジェクトがロックされていることを示します。|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|`unique_lock` のコンストラクターに渡すことのできるオブジェクトを表し、コンストラクターがそれに渡されるミューテックス オブジェクトをロックしないことを示しています。|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|`unique_lock` のコンストラクターに渡すことのできるオブジェクトを表し、ブロックされずに渡される `mutex` をコンストラクターがロック解除しようとすることを示します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
