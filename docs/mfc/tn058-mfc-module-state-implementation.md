---
title: TN058:MFC モジュール状態の実装
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: d803dba36b7790173b21dacb6cb34241f27dfb96
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610957"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058:MFC モジュール状態の実装

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このテクニカル ノートでは、MFC「モジュールの状態」コンストラクトの実装について説明します。 共有 DLL から Dll を MFC を使用してモジュールの状態の実装の理解は重要な (または OLE インプロセス サーバー)。

このノートを読む前に参照してください「の管理モジュールの状態データの MFC モジュール」[新しいドキュメントの作成、Windows、およびビュー](../mfc/creating-new-documents-windows-and-views.md)します。 この記事にはの重要な情報と、このテーマについての概要が含まれています。

## <a name="overview"></a>概要

MFC の状態情報の 3 つの種類があります。モジュールの状態、プロセスの状態、およびスレッドの状態。 場合によってこれらの状態の種類を結合できます。 たとえば、MFC のハンドルのマップは、ローカル モジュールとスレッド ローカルの両方です。 これにより、各スレッドで異なる複数のマップに 2 つの異なるモジュールです。

プロセスの状態およびスレッドの状態は似ています。 これらのデータ項目は、グローバル変数がありましたが、特定のプロセスに固有のもの、またはスレッドの適切な Win32s をサポートする、または適切なマルチ スレッドのサポートのする必要があることです。 カテゴリ内に収まる範囲指定されたデータ項目は、その項目とその目的のセマンティクスに関するプロセスとスレッドの境界によって異なります。

モジュールの状態は一意で真にグローバルな状態またはローカル プロセスまたはスレッド ローカル状態のいずれかを含めることができます。 さらに切り替えることができます簡単にします。

## <a name="module-state-switching"></a>モジュールの状態の切り替え

各スレッドには、「現在」または「アクティブ」のモジュール状態へのポインターが含まれています (当然ながら、ポインターは MFC のスレッド ローカル状態の一部)。 このポインターは、実行のスレッドが OLE コントロール、DLL、または、OLE コントロールを呼び出すアプリケーションを呼び出すアプリケーションなど、モジュール境界を通過するときに変更されます。

呼び出して現在のモジュール状態が切り替えられた`AfxSetModuleState`します。 ほとんどの場合、API と直接対応するかことはありません。 MFC では、多くの場合はそれを呼び出します (WinMain、OLE のエントリ ポイントで`AfxWndProc`など。)。 これは特殊な静的にリンクすることで記述する任意のコンポーネントに`WndProc`、および特殊な`WinMain`(または`DllMain`) どのモジュールの状態は、現在であるかを把握しています。 DLLMODUL を調べることで、このコードを確認できます。CPP または APPMODUL します。CPP mfc \src ディレクトリにします。

モジュールの状態を設定していない設定バックアップすることがまれになります。 独自のモジュールを「プッシュ」時間のほとんどは、として現在の状態で、次に、完了したら、後に「ポップ表示」元のコンテキスト。 これには、マクロを[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)と特殊なクラス`AFX_MAINTAIN_STATE`します。

`CCmdTarget` モジュール状態の切り替えをサポートするための特別な機能があります。 具体的には、 `CCmdTarget` OLE オートメーションおよび OLE COM のエントリ ポイントに使用されるルート クラス。 などの他のエントリ ポイント システムに公開すると、これらのエントリ ポイントは、適切なモジュールの状態を設定する必要があります。 方法は、指定された`CCmdTarget`何「正しい」のモジュール状態であるか、応答は「記憶」、「現在」のモジュール状態が構築したときに、設定できるようにするには、現在のモジュール状態「記憶」その後の値と呼ばれることを確認します。 結果として、モジュールの状態を指定された`CCmdTarget`オブジェクトが関連付けられているでは、オブジェクトを構築したときに現在モジュールの状態。 INPROC サーバーを読み込んで、オブジェクトの作成、およびそのメソッドを呼び出すことの簡単な例を実行します。

1. OLE で DLL のロードを使用して`LoadLibrary`します。

2. `RawDllMain` 最初に呼び出されます。 静的モジュールの既知の状態に、DLL のモジュールの状態を設定します。 このため`RawDllMain`DLL に静的にリンクさせます。

1. このオブジェクトに関連付けられたクラス ファクトリのコンス トラクターが呼び出されます。 `COleObjectFactory` 派生`CCmdTarget`モジュール状態でインスタンス化された結果、記憶しています。 これは重要です — 現在に設定するには、どのようなモジュール状態認識これでクラス ファクトリにオブジェクトを作成することを確認するとき、します。

4. `DllGetClassObject` 呼び出してクラス ファクトリを取得します。 MFC では、このモジュールに関連付けられたクラス ファクトリの一覧を検索し、それを返します。

5. `COleObjectFactory::XClassFactory2::CreateInstance` が呼ばれたとき。 オブジェクトを作成しで返すことで、前にこの関数は手順 3 での現在のモジュール状態にモジュールの状態を設定 (ときに対象だった 1 つ、`COleObjectFactory`がインスタンス化された)。 内のこれは、 [METHOD_PROLOGUE](com-interface-entry-points.md)します。

1. すぎますが、オブジェクトが作成されたときに、`CCmdTarget`派生と同じ方法で`COleObjectFactory`記憶するモジュールの状態がアクティブではこの新しいオブジェクト。 オブジェクトに切り替えるには、どのモジュール状態を認識するようになりましたたびに呼び出されます。

1. クライアントから受信した OLE COM オブジェクトで関数を呼び出すその`CoCreateInstance`呼び出します。 使用して、オブジェクトが呼び出されたときに`METHOD_PROLOGUE`と同じようにモジュールの状態を切り替える`COleObjectFactory`は。

ご覧のように、モジュールの状態が反映されますオブジェクトからオブジェクトが作成されるとき。 モジュールの状態を適切に設定するのには重要です。 設定されていない場合、DLL または COM オブジェクトはから呼び出されて、または、独自のリソースを検索することがない可能性がありますまたはひどい他の方法で障害が発生する MFC アプリケーションと対話が不十分な場合があります。

特定の種類の Dll、具体的には「MFC の拡張機能」Dll がでモジュールの状態を切り替えるできませんに注意してください。 その`RawDllMain`(実際には、通常必要すらありません、 `RawDllMain`)。 これは、場合の動作は"と"がそれらを使用するアプリケーションで実際に存在することを意図しているためにです。 実行されているアプリケーションの一部では非常によくあり、そのアプリケーションのグローバル状態を変更するには、その意図。

OLE コントロールとその他の Dll は非常に異なります。 呼び出し元アプリケーションの状態を変更しません。それらを呼び出しているアプリケーションもあります MFC アプリケーションとのでない可能性がありますを変更する状態。 これは、モジュールの状態の切り替えが採用する理由です。

DLL のダイアログ ボックスを起動するなどの DLL からエクスポートされた関数の関数の先頭に次のコードを追加する必要があります。

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

モジュールの現在の状態から返された状態と交換この[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)現在のスコープが終わるまでです。

AFX_MODULE_STATE マクロを使用しない場合は、Dll 内のリソースに問題が発生します。 既定では、MFC では、メイン アプリケーションのリソース ハンドルを使用して、リソースのテンプレートを読み込みます。 このテンプレートは、DLL に実際に格納されます。 根本原因は、MFC のモジュールの状態情報がいない AFX_MODULE_STATE マクロによって切り替えられたことです。 リソース ハンドルが MFC のモジュール状態から復旧します。 モジュールの状態が切り替えられていないすると、間違ったリソース ハンドルが使用されます。

AFX_MODULE_STATE は、すべての関数は DLL 内に配置する必要はありません。 たとえば、 `InitInstance` MFC モジュールの直前の状態を自動的に移動するために呼び出すことがなくアプリケーションの MFC コードによって呼び出されることができます`InitInstance`とスイッチの後に、再度、`InitInstance`を返します。 すべてのメッセージ マップ ハンドラーも同様です。 レギュラー MFC Dll があるすべてのメッセージをルーティングする前に、モジュールの状態を自動的に切り替わる特殊なマスター ウィンドウ プロシージャ。

## <a name="process-local-data"></a>ローカル データの処理

ローカル データを処理できませんこのような大きな懸念 Win32s DLL モデルの難しさのないされていた。 Win32s では、すべての Dll は、複数のアプリケーションによって読み込まれるときにさらに、グローバルなデータを共有します。 これは、各 DLL が DLL にアタッチする各プロセスでは、そのデータ領域の個別のコピーを取得、「実際の」Win32 DLL データ モデルとは大きく異なります。 に、複雑さを追加するには、Win32s DLL 内のヒープに割り当てられたデータ実際には特定のプロセス (少なくとも限り所有権)。 次のデータとコードを検討してください。

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

何が起きるかどうか、上記のコード内にある DLL および DLL が A と B (ある可能性があります、実際には、同じアプリケーションの 2 つのインスタンス) の 2 つのプロセスによって読み込まれています。 呼び出し`SetGlobalString("Hello from A")`します。 メモリが割り当てられている結果として、`CString`注意注意して A. プロセスのコンテキスト内のデータ、`CString`自体はグローバルとが両方に表示されると BB を呼び出す`GetGlobalString(sz, sizeof(sz))`します。 B はデータ セットを表示することになります。 Win32s は Win32 にはなどのプロセス間の保護を提供しないためにです。 最初の問題があります。多くの場合に、別のアプリケーションによって所有されていることと見なされるグローバル データに影響を与える 1 つのアプリケーションには望ましくありません。

追加でも問題があります。 たとえば、今すぐに終了するとします。 A が終了したときで使用されるメモリの '`strGlobal`' 文字列は、システムの利用可能になって、オペレーティング システムがプロセス A によって割り当てられたすべてのメモリを自動的に解放は、します。 は解放されず、`CString`デストラクターが呼び出されます。 まだ呼び出されていません。 単純に解放されるため、割り当てられているアプリケーションが終了します。 ここで B `GetGlobalString(sz, sizeof(sz))`、有効なデータが利用できません。 その他のアプリケーションが、他の情報をそのメモリを使用している可能性があります。

明らかに問題が存在します。 MFC 3.x がスレッド ローカル ストレージ (TLS) と呼ばれる手法を使用します。 MFC 3.x をそれを呼び出さない場合でも、win32s 本当に、プロセスのローカル記憶域インデックスとして機能する TLS インデックスを割り当てます、し、その TLS インデックスに基づくすべてのデータを参照します。 これは Win32 ではスレッド ローカル データの格納に使用された TLS インデックスに似ています (そのサブジェクトの詳細については後述します)。 これにより、プロセスごとに少なくとも 2 つの TLS インデックスを利用するすべての MFC DLL が発生します。 Dll を読み込む多く OLE コントロール (Ocx) を考慮するときに、(は 64 にのみ使用可能な) TLS インデックスからすばやくで実行します。 さらに、MFC では、1 つの構造内の 1 か所ですべてのデータを配置する必要があります。 非常に拡張できませんでしたし、TLS インデックスの使用に関して最適でした。

MFC 4.x の一連のプロセスがローカルにする必要があるデータを「ラップ」できますクラス テンプレートとこれが対処します。 たとえば、上記で説明した問題を解決して、記述することで可能性があります。

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC では、2 つの手順でこれを実装します。 まず、Win32 の上にレイヤーがある__Tls\*__  Api (**TlsAlloc**、 **TlsSetValue**、 **TlsGetValue**など) をある Dll の数に関係なく、プロセスごとに 2 つだけの TLS インデックスを使用します。 2 番目、`CProcessLocal`このデータにアクセスするテンプレートが提供されます。 演算子をオーバーライドできますように直感的な構文である]-> [です。 すべてのオブジェクトによってラップされている`CProcessLocal`から派生する必要があります`CNoTrackObject`します。 `CNoTrackObject` 下位レベルのアロケーターを提供します (**LocalAlloc**/**LocalFree**) と仮想デストラクターをプロセスが終了したときに、MFC はプロセスのローカル オブジェクトを破棄自動的にできます。 このようなオブジェクトは、追加のクリーンアップが必要な場合、カスタム デストラクターを持つことができます。 上記の例では、コンパイラは、埋め込みを破棄する既定のデストラクターを生成するため`CString`オブジェクト。

この方法の他の興味深い利点があります。 いるだけでなく、すべて`CProcessLocal`オブジェクトが自動的には、破棄が必要になるまでにないが構築されます。 `CProcessLocal::operator->` 初めて呼び出されると、関連付けられたオブジェクトとありません早くをインスタンス化されます。 したがって、上記の例では、'`strGlobal`' 文字列は、最初の時刻までは作成されません`SetGlobalString`または`GetGlobalString`が呼び出されます。 場合によっては、DLL のスタートアップ時間を短縮これは役立ちます。

## <a name="thread-local-data"></a>スレッド ローカル データ

ローカル データの処理と同様に、スレッド ローカル データがする際、データは、特定のスレッドにローカルである必要があります。 つまり、そのデータにアクセスする各スレッドのデータの個別のインスタンスが必要です。 これは、何度も使用できますの広範な同期機構を使用せずに。 場合は、データは、複数のスレッドで共有する必要はありません、このようなメカニズムがあります。 高価で不要です。 あると、 `CString` (上記の例のように多く) オブジェクト。 せることさえできるスレッドのローカルでラップすることによって、`CThreadLocal`テンプレート。

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

場合`MakeRandomString`が呼び出された 2 つの異なるスレッドからそれぞれが「シャッフル」文字列さまざまな方法で両者を妨げることはありません。 これがあるため、実際には`strThread`1 つのグローバル インスタンスではなく、スレッドごとのインスタンス。

参照を使用してキャプチャする方法に注意してください、`CString`アドレス 1 回の代わりに 1 回あたりループの反復処理します。 ループのコードに書き込まれた可能性があります`threadData->strThread`everywhere '`str`' を使用するが、コードが実行に時間がかかります。 ループ内でこのような参照が発生したときに、データへの参照をキャッシュすることをお勧めします。

`CThreadLocal`クラス テンプレートと同じメカニズムを使用している`CProcessLocal`と実装のと同じ手法です。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
