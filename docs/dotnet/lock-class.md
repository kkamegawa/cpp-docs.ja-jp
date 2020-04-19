---
title: lock クラス
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 43418da36aa2d87608a9d672e4345d24011be0b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153441"
---
# <a name="lock-class"></a>lock クラス

このクラスは、複数のスレッドからオブジェクトにアクセスを同期するためのロックの取得を自動化します。  作成されるときにロックを取得し、リリースが破棄されるとロック。

## <a name="syntax"></a>構文

```cpp
ref class lock;
```

## <a name="remarks"></a>Remarks

`lock` CLR オブジェクトに対してのみ使用できますが、CLR コードでのみ使用できます。

ロックのクラスは内部的には、<xref:System.Threading.Monitor>アクセスを同期します。 詳細については、参照先の記事を参照してください。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|---------|-----------|
|[lock::lock](#lock)|構築、`lock`必要に応じて一定の時間、またはすべてではなく、永久にロックの取得を待機しているオブジェクト。|
|[lock::~lock](#tilde-lock)|Destructs、`lock`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|---------|-----------|
|[lock::acquire](#acquire)|必要に応じて一定の時間、またはすべてではなく、永久にロックの取得を待機しているオブジェクトのロックを取得します。|
|[lock::is_locked](#is-locked)|ロックが保持されているかどうかを示します。|
|[lock::release](#release)|ロックを解放します。|
|[lock::try_acquire](#try-acquire)|一定の時間を待機していると、返すオブジェクトのロックを取得、`bool`例外をスローする代わりに取得の成功を報告します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|---------|-----------|
|[lock::operator&nbsp;bool](#operator-bool)|使用するための演算子`lock`条件式。|
|[lock::operator==](#operator-equality)|等値演算子。|
|[lock::operator!=](#operator-inequality)|非等値演算子。|

## <a name="requirements"></a>必要条件

**ヘッダー ファイル** \<msclr\lock.h >

**Namespace** msclr



## <a name="lock"></a>lock::lock

構築、`lock`必要に応じて一定の時間、またはすべてではなく、永久にロックの取得を待機しているオブジェクト。

```cpp
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

### <a name="parameters"></a>パラメーター

*_object*<br/>
ロックするオブジェクト。

*_timeout*<br/>
タイムアウト値 (ミリ秒単位) またはとして、<xref:System.TimeSpan>します。

### <a name="exceptions"></a>例外

スロー<xref:System.ApplicationException>ロック取得がタイムアウトする前に発生しない場合。

### <a name="remarks"></a>Remarks

コンス トラクターの最初の 3 つのロックを取得しようとしました。 `_object` 、指定されたタイムアウト期間内 (または<xref:System.Threading.Timeout.Infinite>が指定されない場合)。

4 番目のコンス トラクターの形式に対するロックの取得は`_object`します。 `lock_later` メンバーである、 [lock_when 列挙型](../dotnet/lock-when-enum.md)します。 使用[lock::acquire](../dotnet/lock-acquire.md)または[lock::try_acquire](../dotnet/lock-try-acquire.md)ここで、ロックを取得します。

デストラクターが呼び出されたときに、ロックが自動的に解放されます。

`_object` ことはできません<xref:System.Threading.ReaderWriterLock>します。  場合は、コンパイラ エラーが発生します。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。 クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。 メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 その後、メイン アプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_lock.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="tilde-lock"></a>ロック:: ~ ロック

Destructs、`lock`オブジェクト。

```cpp
~lock();
```

### <a name="remarks"></a>Remarks

デストラクターの呼び出し[lock::release](../dotnet/lock-release.md)します。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。  クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。  メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 その後、メイン アプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_dtor.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="acquire"></a>lock::acquire

必要に応じて一定の時間、またはすべてではなく、永久にロックの取得を待機しているオブジェクトのロックを取得します。

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>パラメーター

*_timeout*<br/>
タイムアウト値 (ミリ秒単位) またはとして、<xref:System.TimeSpan>します。

### <a name="exceptions"></a>例外

スロー<xref:System.ApplicationException>ロック取得がタイムアウトする前に発生しない場合。

### <a name="remarks"></a>Remarks

タイムアウト値が指定されていない場合、既定タイムアウトは<xref:System.Threading.Timeout.Infinite>します。

場合は、ロックは既に取得されて、何もされません。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。  クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。 メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 その後、メイン アプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="is-locked"></a>lock::is_locked

ロックが保持されているかどうかを示します。

```cpp
bool is_locked();
```

### <a name="return-value"></a>戻り値

`true` ロックが保持されている場合`false`それ以外の場合。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。  クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。  メイン アプリケーション スレッドは、すべてのワーカー スレッドがまだ存在していて、そのタスクが完了するまでのすべてのワーカー スレッドの終了を待機を定期的に確認するクラスの同じインスタンスでロックを使用します。

```cpp
// msl_lock_is_locked.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l.is_locked()) { // check if we got the lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="operator-bool"></a>lock::operator bool

使用するための演算子`lock`条件式。

```cpp
operator bool();
```

### <a name="return-value"></a>戻り値

`true` ロックが保持されている場合`false`それ以外の場合。

### <a name="remarks"></a>Remarks

実際にこの演算子の変換`_detail_class::_safe_bool`よりも安全である`bool`整数型に変換できないためです。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。  クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。 メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 メインのアプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_op_bool.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l) { // use bool operator to check for lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="release"></a>lock::release

ロックを解放します。

```cpp
void release();
```

### <a name="remarks"></a>Remarks

ロックが保持されていない場合`release`何も行われません。

この関数を明示的に呼び出す必要はありません。 ときに、`lock`オブジェクトが、そのデストラクターの呼び出しのスコープ外になる`release`します。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。 クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。 メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 その後、メイン アプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_release.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="try-acquire"></a>lock::try_acquire

一定の時間を待機していると、返すオブジェクトのロックを取得、`bool`例外をスローする代わりに取得の成功を報告します。

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>パラメーター

*_timeout*<br/>
タイムアウト値 (ミリ秒単位) またはとして、<xref:System.TimeSpan>します。

### <a name="return-value"></a>戻り値

`true` ロックが取得された場合`false`それ以外の場合。

### <a name="remarks"></a>Remarks

場合は、ロックは既に取得されて、何もされません。

### <a name="example"></a>例

この例では、複数のスレッド クラスの 1 つのインスタンスを使用します。 クラスは、その内部データへのアクセスがスレッドごとに一貫性があるかどうかを確認する自体のロックを使用します。 メイン アプリケーション スレッドを定期的にチェックして、任意のワーカー スレッドがまだ存在クラスの同じインスタンス上のロックを使用します。 その後、メイン アプリケーションは、すべてのワーカー スレッドがタスクを完了するまでは終了を待機します。

```cpp
// msl_lock_try_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="operator-equality"></a>lock::operator==

等値演算子。

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>パラメーター

*t*<br/>
等しいかどうかを比較するオブジェクト。

### <a name="return-value"></a>戻り値

返します`true`場合`t`はロックのオブジェクトと同じ`false`それ以外の場合。

### <a name="example"></a>例

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="operator-inequality"></a>lock::operator!=

非等値演算子。

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>パラメーター

*t*<br/>
非等値を比較するオブジェクト。

### <a name="return-value"></a>戻り値

返します`true`場合`t`ロックのオブジェクトとは異なります`false`それ以外の場合。

### <a name="example"></a>例

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```