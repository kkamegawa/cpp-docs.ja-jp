---
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: bd5df2917d377e7bc119d1aa85a32c4d5149c305
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686435"
---
# <a name="ltshared_mutex"></a>&lt;shared_mutex >

@No__t_0shared_mutex > ヘッダーには、複数のスレッドからアクセスできる共有データを保護する同期プリミティブが用意されています。 ミューテックス クラスで提供される排他アクセス制御だけでなく、共有ミューテックス クラスによって非排他的なアクセス用の複数のスレッドによる共有所有権も可能になります。 共有ミューテックスを使用して、競合状態を発生させず複数のスレッドで読み取ることができるリソースを制御できますが、共有ミューテックスは 1 つのスレッドによって排他的に書き込まれる必要があります。

ヘッダー &lt;shared_mutex > では、クラス `shared_mutex` および `shared_timed_mutex`、クラステンプレート `shared_lock`、および共有ミューテックスをサポートするためのテンプレート関数 `swap` が定義されています。

|クラス|説明|
|-------------|-----------------|
|[shared_mutex クラス](#class_shared_mutex)|1 つのエージェントによって排他的にロックされるか、または複数のエージェントで非排他的に共有される共有 mutex 型。|
|[shared_timed_mutex クラス](#class_shared_timed_mutex)|1 つのエージェントによって排他的にロックされるか、または複数のエージェントで非排他的に共有される共有 timed mutex 型。|
|[shared_lock クラス](#class_shared_lock)|共有ミューテックスをラップして、一定のロック操作と複数のエージェントによる非排他的な共有をサポートするクラステンプレート。|

|関数|説明|
|---------------|-----------------|
|[swap](#function_swap)|関数のパラメーターによって参照される共有ミューテックス オブジェクトの内容を交換します。|

## <a name="syntax"></a>構文

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Remarks

クラス `shared_mutex` のインスタンスは、*共有 mutex 型*、つまり、スコープ内でのミューテックスの共有所有権を制御する型です。 共有 mutex 型は、mutex 型および共有の非排他的な所有権をサポートするためのメンバーの要件をすべて満たしています。

共有 mutex 型は、追加のメソッド `lock_shared`、`unlock_shared`、および `try_lock_shared` をサポートします。

- `lock_shared` メソッドは、スレッドがミューテックスの共有所有権を取得するまでそのスレッドの呼び出しをブロックします。

- `unlock_shared` メソッドは、スレッドの呼び出しによって保持されるミューテックスの共有所有権を解放します。

- `try_lock_shared` メソッドは、ミューテックスをブロックせずに共有所有権を取得しようとします。 戻り値の型は**ブール**型に変換でき、メソッドが所有権を取得した場合は**true**になりますが、それ以外の場合は**false**になります。

クラス `shared_timed_mutex` は、*共有 timed mutex 型*、つまり、共有 mutex 型と timed mutex 型の両方の要件を満たす型です。

共有 timed mutex 型は、追加のメソッド `try_lock_shared_for` および `try_lock_shared_until` をサポートします。

- `try_lock_shared_for` メソッドは、パラメーターで指定した期間が経過するまで、ミューテックスの共有所有権を取得しようとします。 この期間が正ではない場合、このメソッドは `try_lock_shared` と等しくなります。 このメソッドは、共有所有権を取得しない限り、指定した期間内では返しません。 メソッドが所有権を取得した場合、その戻り値は**true**になりますが、それ以外の場合は**false**になります。

- `try_lock_shared_until` メソッドは、指定された絶対時間が経過するまで、ミューテックスの共有所有権を取得しようとします。 指定した時間が既に経過している場合、このメソッドは `try_lock_shared` と等しくなります。 このメソッドは、共有所有権を取得しない限り、指定した時間の前に返しません。 メソッドが所有権を取得した場合、その戻り値は**true**になりますが、それ以外の場合は**false**になります。

@No__t_0 クラステンプレートを使用すると、時間を指定したロックと所有権を共有ミューテックスに転送するためのサポートが拡張されます。 ミューテックスの所有権は構築時または構築後に取得でき、別の `shared_lock` オブジェクトに転送できます。 `shared_lock` 型のオブジェクトは移動できますが、コピーできません。

> [!WARNING]
> Visual Studio 2015 以降では、 C++標準ライブラリの同期の種類は windows 同期プリミティブに基づいており、concrt を使用しなくなりました (ターゲットプラットフォームが windows XP の場合を除く)。 @No__t_0shared_mutex > で定義されている型は、ConcRT 型または関数では使用できません。

## <a name="classes"></a>クラス

###  <a name="class_shared_mutex"></a> shared_mutex クラス

クラス `shared_mutex` は、共有所有権セマンティクスで非再帰的なミューテックスを実装します。

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex クラス

クラス `shared_timed_mutex` は、timed mutex 型の要件を満たしている共有所有権セマンティクスで非再帰的なミューテックスを実装します。

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="class_shared_lock"></a> shared_lock クラス

クラステンプレート `shared_lock` は、スコープ内の共有ミューテックスオブジェクトの共有所有権を制御します。 テンプレート パラメーターは、共有 mutex 型である必要があります。

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>関数

###  <a name="function_swap"></a>フォト

`shared_lock` オブジェクトを交換します。

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

2 つの `shared_lock` オブジェクトの内容を交換します。 実質的に `x.swap(y)` と同じです。

## <a name="requirements"></a>［要件］

**ヘッダー:** &lt;shared_mutex>

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[&lt;mutex>](../standard-library/mutex.md)
