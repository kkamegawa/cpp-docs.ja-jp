---
title: マルチスレッド:作成 (MFC ユーザーインターフェイススレッドを)
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512090"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>マルチスレッド:作成 (MFC ユーザーインターフェイススレッドを)

ユーザー インターフェイス スレッドでは、主にユーザー入力を処理し、ユーザーが生成したイベントに応答します。この処理は、アプリケーションのほかの部分を実行しているスレッドとは無関係に行われます。 `CWinApp` の派生クラスで提供されるメイン アプリケーション スレッドは、既に生成され実行を開始しています。 このトピックでは、ユーザー インターフェイス スレッドを作成するための手順について説明します。

ユーザーインターフェイススレッドを作成する場合は、まず、 [CWinThread](../mfc/reference/cwinthread-class.md)からクラスを派生させる必要があります。 [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)マクロと[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)マクロを使用して、このクラスを宣言して実装する必要があります。 このクラスでは、一部の関数をオーバーライドする必要があります。また、他の関数も必要に応じてオーバーライドできます。 次の表に、各関数とその用途を示します。

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>ユーザー インターフェイス スレッドを作成するためにオーバーライドする関数

|関数|目的|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|スレッド終了時の後処理を行います。 通常、オーバーライドします。|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|スレッドのインスタンスを初期化します。 必ずオーバーライドします。|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|スレッド固有のアイドル処理ハンドラーを行います。 通常、オーバーライドしません。|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|とに`TranslateMessage`ディスパッチされる前に、 `DispatchMessage`メッセージをフィルター処理します。 通常、オーバーライドしません。|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|スレッドのメッセージ ハンドラーおよびコマンド ハンドラーがスローした未処理例外を受け取ります。 通常、オーバーライドしません。|
|[[実行]](../mfc/reference/cwinthread-class.md#run)|スレッドの制御関数です。 メッセージ ポンプが含まれます。 この関数をオーバーライドすることはほとんどありません。|

MFC は、パラメーターのオーバーロードによって `AfxBeginThread` の 2 つのバージョンを提供します。1 つはワーカー スレッドのみを作成でき、もう 1 つは、ユーザー インターフェイス スレッドまたはワーカー スレッドを作成できます。 ユーザーインターフェイススレッドを開始するには、 [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)の2番目のオーバーロードを呼び出して、次の情報を指定します。

- から`CWinThread`派生したクラスの[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) 。

- (省略可) 目的の優先順位。 既定の優先順位は normal です。 使用可能な優先度レベルの詳細については、Windows SDK の「 [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 」を参照してください。

- (省略可) スレッドのスタック サイズ。 既定値は、このスレッドを生成するスレッドのスタックと同じサイズです。

- OptionalCREATE_SUSPENDED は、スレッドを中断状態で作成する場合に使用します。 既定値 0 では、スレッドを通常どおり起動します。

- (省略可) セキュリティ属性。 既定では親スレッドと同じ値になります。 このセキュリティ情報の形式の詳細については、Windows SDK の「 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 」を参照してください。

`AfxBeginThread` は、スレッド生成処理の大部分を自動的に行います。 クラスの新しいオブジェクトを作成し、指定した情報を使用して初期化し、 [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread)を呼び出してスレッドの実行を開始します。 なんらかの原因でスレッド生成に失敗すると、スレッド生成処理全体をチェックし、すべてのオブジェクトを確実に解放します。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [マルチスレッド: スレッドの終了](multithreading-terminating-threads.md)

- [マルチスレッド: マルチスレッド : ワーカー スレッドの作成](multithreading-creating-worker-threads.md)

- [プロセスとスレッド](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>関連項目

[C++ と MFC を使用するマルチスレッド](multithreading-with-cpp-and-mfc.md)
