---
title: MFC での MAPI サポート
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: e46eaf2bd84d4cebd2215ab2752ce3bb8e1eb9b3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907677"
---
# <a name="mapi-support-in-mfc"></a>MFC での MAPI サポート

MFC では、クラス`CDocument`の Microsoft メッセージングアプリケーションプログラムインターフェイス (MAPI) のサブセットがサポートされています。 具体的に`CDocument`は、には、メールサポートがエンドユーザーのコンピューターに存在するかどうかを判断するメンバー関数があり、その場合は、標準のコマンド ID が ID_FILE_SEND_MAIL であるメール送信コマンドを有効にします。 このコマンドの MFC ハンドラー関数を使用すると、電子メールでドキュメントを送信できます。

> [!TIP]
>  MFC では MAPI 関数セット全体がカプセル化されませんが、MFC プログラムから直接 Win32 API 関数を呼び出すことができるのと同じように、MAPI 関数を直接呼び出すことができます。

アプリケーションで [メールの送信] コマンドを指定するのは非常に簡単です。 MFC には、ドキュメント ( `CDocument`つまり、から派生したオブジェクト) を添付ファイルとしてパッケージ化し、それをメールとして送信するための実装が用意されています。 この添付ファイルは、ドキュメントの内容を電子メールメッセージに保存 (シリアル化) する、ファイルの保存コマンドに相当します。 この実装では、ユーザーのコンピューター上のメールクライアントでを呼び出して、メールアドレスを指定したり、件名やメッセージのテキストをメールメッセージに追加したりできるようにします。 ユーザーには、使い慣れたメールアプリケーションのユーザーインターフェイスが表示されます。 この機能は`CDocument` `OnFileSendMail` 、と`OnUpdateFileSendMail`の2つのメンバー関数によって提供されます。

MAPI は、添付ファイルを送信するためにファイルを読み取る必要があります。 `OnFileSendMail`関数呼び出し中にアプリケーションがデータファイルを開いたままにする場合は、ファイルを共有モードで開いて、複数のプロセスがファイルにアクセスできるようにする必要があります。

> [!NOTE]
>  For クラス`OnFileSendMail` `COleDocument`のオーバーライドバージョンは、複合ドキュメントを正しく処理します。

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>MFC でメール送信コマンドを実装するには

1. Visual C++ menu editor を使用して、コマンド ID が ID_FILE_SEND_MAIL のメニュー項目を追加します。

   このコマンド ID は、AFXRES.H のフレームワークによって提供されます。始め. コマンドは任意のメニューに追加できますが、通常は **[ファイル]** メニューに追加されます。

1. ドキュメントのメッセージマップに次のコードを手動で追加します。

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  このメッセージマップは、または`CDocument` `COleDocument`のいずれかから派生したドキュメントに対して機能します。メッセージマップが派生ドキュメントクラスにある場合でも、どちらの場合も正しい基本クラスを取得します。

1. アプリケーションをビルドします。

メールサポートが利用可能な場合、MFC では、 `OnUpdateFileSendMail`でメニュー項目を有効に`OnFileSendMail`し、その後でコマンドをで処理します。 メールサポートが利用できない場合は、ユーザーがメニュー項目を表示しないように、MFC によって自動的に削除されます。

> [!TIP]
>  前に説明したようにメッセージマップエントリを手動で追加するのではなく、クラス[クラスウィザード](reference/mfc-class-wizard.md)を使用して、メッセージを関数にマップできます。 詳細については、「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください。

関連情報については、「 [MAPI](../mfc/mapi.md)の概要」を参照してください。

MAPI を有効にする`CDocument`メンバー関数の詳細については、以下を参照してください。

- [CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument:: OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>関連項目

[MAPI](../mfc/mapi.md)
