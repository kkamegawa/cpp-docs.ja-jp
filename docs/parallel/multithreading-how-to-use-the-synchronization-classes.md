---
title: 'マルチスレッド: MFC 同期クラスの使用方法'
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
ms.openlocfilehash: ef76199813de417d2aa57eb7f3f15ae4d2fefc56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140504"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>マルチスレッド: MFC 同期クラスの使用方法

リソースにアクセスする複数のスレッドの同期は、マルチスレッド アプリケーションを書くときに共通の問題です。 複数のスレッドから同じデータに同時にアクセスすると、予測できない結果になることがあります。 たとえば、あるスレッドで構造体の内容を更新しているときに、別のスレッドが同じ構造体の内容を読み取るということが考えられます。 この場合、後者のスレッドが実際に読み取った内容が、古いデータになるか更新後のデータになるかはわかりません。古いデータと更新データが混在することも考えられます。 MFC (Microsoft Foundation Class) の同期クラスと同期アクセス クラスを使うと、この問題を解決できます。 このトピックでは、これらのクラスを使用して、一般的なマルチスレッド アプリケーションでスレッド セーフなクラスを作成する方法を説明します。

一般的なマルチスレッド アプリケーションには、スレッド間の共有リソースを表すクラスがあります。 スレッドセーフなクラスをデザインすると、同期関数を呼び出す必要がありません。 リソースへのアクセスをすべてクラス内部で処理するので、プログラマはクラスの破損などを気にせずに、クラスを最大限に活用する方法だけを考えることができます。 スレッド セーフなクラスを作成するには、同期クラスをリソース クラス内にマージすることが効果的な方法です。 同期クラスの共有クラスへのマージは簡単に行うことができます。

たとえば、アカウントのリンク リストを保持するアプリケーションの場合を考えます。 このアプリケーションでは 3 つまでのアカウントを個別のウィンドウで調べることができます。ただし、一度に更新できるアカウントは 1 つだけとします。 更新されたデータはネットワークを通じてデータ アーカイブに送られます。

このアプリケーションでは、3 種類の同期クラスをすべて使います。 最大3つのアカウントを一度に調べることができるので、この方法では、3つのビューオブジェクトへのアクセスを制限するために[CSemaphore](../mfc/reference/csemaphore-class.md)が使用されます。 4 番目のアカウントを表示しようとすると、アプリケーションは最初の 3 つのウィンドウのいずれかが閉じるのを待つか、失敗します。 アカウントが更新されると、アプリケーションは[CCriticalSection](../mfc/reference/ccriticalsection-class.md)を使用して、一度に1つのアカウントのみが更新されるようにします。 更新が成功すると、そのイベントがシグナル状態になるのを待機しているスレッドを解放するために、 [CEvent](../mfc/reference/cevent-class.md)にシグナルを送ります。 新しいデータは、このスレッドからデータ アーカイブに送られます。

## <a name="_mfc_designing_a_thread.2d.safe_class"></a>スレッドセーフなクラスの設計

スレッドセーフなクラスにするには、まず、該当する同期クラスをデータ メンバーとして共有クラスに追加します。 前のアカウント管理の例では、`CSemaphore` データメンバーがビュークラスに追加され、`CCriticalSection` データメンバーがリンクリストクラスに追加され、`CEvent` データメンバーがデータストレージクラスに追加されます。

次に、クラス内のデータを変更する、または被制御リソースにアクセスするすべてのメンバー関数への同期呼び出しを追加します。 各関数では、 [CSingleLock](../mfc/reference/csinglelock-class.md)オブジェクトまたは[CMultiLock](../mfc/reference/cmultilock-class.md)オブジェクトを作成し、そのオブジェクトの `Lock` 関数を呼び出す必要があります。 ロック オブジェクトがスコープ外に出て破棄されると、このオブジェクトのデストラクターによって `Unlock` が呼び出され、リソースが解放されます。 必要に応じて、`Unlock` を直接呼び出すこともできます。

このようにスレッド セーフなクラスをデザインすると、非スレッド セーフなクラスと同じように、マルチスレッド アプリケーションで簡単に使用できるだけでなく、安全性も保証されます。 同期オブジェクトと同期アクセス オブジェクトをリソースのクラスにカプセル化すると、同期コードを使わずに、スレッドを安全に使用できます。

次のコード例では、共有リソース クラスで宣言されたデータ メンバー `m_CritSection` (`CCriticalSection` 型) と `CSingleLock` オブジェクトを使って、この方法を示します。 `CWinThread` から派生する共有リソースの同期は、`CSingleLock` オブジェクトのアドレスを使って `m_CritSection` オブジェクトを作成することによって行います。 まず、リソースのロックを行い、ロックを取得すると、共有オブジェクト側の作業は完了です。 作業が完了すると、`Unlock` 呼び出しによってリソースのロックが解除されます。

```cpp
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection` には、その他の MFC 同期クラスと異なり、期限付きのロック要求オプションがありません。 スレッドが解放されるまでの待機時間は無限です。

この手法の欠点は、同期オブジェクトを追加しない場合と比べて、クラスの動作が少し遅くなることです。 また、同期オブジェクトを複数のスレッドで削除した場合は、マージが成功するとは限りません。 このような場合は、同期オブジェクトを別個に管理します。

さまざまな状況で使用する同期クラスを決定する方法の詳細については、「[マルチスレッド: 同期クラスを使用する場合](multithreading-when-to-use-the-synchronization-classes.md)」を参照してください。 同期の詳細については、「Windows SDK での[同期](/windows/win32/Sync/synchronization)」を参照してください。 MFC でのマルチスレッドのサポートの詳細については、「」 [ C++および「Mfc でのマルチスレッド](multithreading-with-cpp-and-mfc.md)」を参照してください。

## <a name="see-also"></a>参照

[C++ と MFC を使用するマルチスレッド](multithreading-with-cpp-and-mfc.md)
