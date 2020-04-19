---
title: CSocketFile クラス
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502447"
---
# <a name="csocketfile-class"></a>CSocketFile クラス

Windows ソケットを使ったネットワーク間でのデータの送受信に使われる `CFile` オブジェクトです。

## <a name="syntax"></a>構文

```
class CSocketFile : public CFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSocketFile:: CSocketFile](#csocketfile)|`CSocketFile` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

このために、 `CSocketFile`オブジェクト`CSocket`をオブジェクトにアタッチできます。 `CSocketFile` オブジェクト`CArchive`をオブジェクトにアタッチして、MFC のシリアル化を使用したデータの送受信を簡略化することもできます。

データをシリアル化 (送信) するには、そのデータをアーカイブに`CSocketFile`挿入します。これは、 `CSocket`メンバー関数を呼び出して、オブジェクトにデータを書き込みます。 データを逆シリアル化 (受信) するには、アーカイブから抽出します。 これにより、アーカイブが`CSocketFile`メンバー関数を呼び出して、 `CSocket`オブジェクトからデータを読み取るようにします。

> [!TIP]
>  ここで`CSocketFile`説明するように、を使用するだけでなく、基本クラスの場合と同様`CFile`に、スタンドアロンのファイルオブジェクトとしても使用できます。 また、をアーカイブ`CSocketFile`ベースの MFC シリアル化関数と共に使用することもできます。 は`CSocketFile` 、の`CFile`すべての機能をサポートしているわけではないため、一部`CSocketFile`の既定の MFC シリアル化関数はと互換性がありません。 これは、クラスに`CEditView`特に当てはまります。 を`CEditView`使用し`CSocketFile` `CArchive` て`CEditView::SerializeRaw`オブジェクトにアタッチされたオブジェクトを介してデータをシリアル`CEditView::Serialize`化することは避けてください。代わりに、を使用してください。 関数では、ファイルオブジェクトに、が含まれて`Seek` `CSocketFile`いないなどの関数があることを想定しています。 `SerializeRaw`

`CArchive`と`CSocketFile` `PumpMessages(FD_READ)`を一緒に使用すると、によって ( `CSocket::Receive` ) によって要求されたバイト数の待機が開始される状況が発生する可能性があります。 `CSocket` これは、Windows ソケットは FD_READ 通知ごとに1つの recv 呼び出し`CSocketFile`しか`CSocket`許可せず、FD_READ ごとに複数の recv 呼び出しを許可するためです。 読み取るデータがないときに FD_READ を取得すると、アプリケーションがハングします。 別の FD_READ が得られない場合、アプリケーションはソケット経由の通信を停止します。

この問題は、次のように解決できます。 ソケットクラスの`CAsyncSocket::IOCtl(FIONREAD, ...)` `Serialize`メソッドで、ソケットから読み取られると予想されるデータが1つの TCP パケット (ネットワークメディアの最大転送単位) のサイズを超えたときに、メッセージクラスのメソッドを呼び出す前に、を呼び出します。 `OnReceive`(通常は1096バイト以上)。 使用可能なデータのサイズが必要以上に満たない場合は、すべてのデータが受信されるのを待ってから、読み取り操作を開始します。

次の例では`m_dwExpected` 、は、ユーザーが受け取ると予想されるおおよそのバイト数です。 コード内の他の場所で宣言することを前提としています。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

詳細については、「 [MFC の windows ソケット](../../mfc/windows-sockets-in-mfc.md)、 [windows ソケット:](../../mfc/windows-sockets-using-sockets-with-archives.md) [Windows sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)だけでなく、アーカイブでソケットを使用します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxsock

##  <a name="csocketfile"></a>CSocketFile:: CSocketFile

`CSocketFile` オブジェクトを構築します。

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>パラメーター

*pSocket*<br/>
`CSocketFile`オブジェクトにアタッチするソケット。

*bArchiveCompatible*<br/>
ファイルオブジェクトが`CArchive`オブジェクトで使用されるかどうかを指定します。 スタンドアロン`CSocketFile` `CFile`のオブジェクトと同じようにスタンドアロンの方法でオブジェクトを使用する場合にのみ、FALSE を渡します。特定の制限事項があります。 このフラグは、 `CArchive` `CSocketFile`オブジェクトにアタッチされているオブジェクトが読み取り用のバッファーを管理する方法を変更します。

### <a name="remarks"></a>Remarks

オブジェクトのデストラクターは、オブジェクトがスコープ外に出るか削除されるときに、ソケットオブジェクトとの関連付けを解除します。

> [!NOTE]
>  は`CSocketFile` 、 `CArchive`オブジェクトなしで (制限された) ファイルとして使用することもできます。 既定では、 `CSocketFile`コンストラクターの*bArchiveCompatible*パラメーターは TRUE です。 これは、ファイルオブジェクトがアーカイブで使用されることを指定します。 アーカイブのないファイルオブジェクトを使用するには、 *bArchiveCompatible*パラメーターに FALSE を渡します。

"アーカイブ互換" モードでは、オブジェクト`CSocketFile`を使用すると、パフォーマンスが向上し、"デッドロック" の危険性が軽減されます。 デッドロックは、送信側と受信側の両方のソケットが互いに待機している場合、または共通のリソースの場合に発生します。 このような状況は、 `CArchive`オブジェクトが`CFile`オブジェクトを`CSocketFile`使用して動作する場合に発生する可能性があります。 で`CFile`は、要求されたバイト数よりも多くのバイトを受信した場合、ファイルの終わりに達したと見なすことができます。

ただし`CSocketFile`、では、データはメッセージベースであり、バッファーには複数のメッセージを含めることができます。したがって、受信したバイト数よりも少なくともファイルの終端を示すことはできません。 この場合、アプリケーションはと`CFile`同様にブロックしません。バッファーが空になるまで、バッファーからのメッセージの読み取りを続行できます。 [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)関数は、このような場合にアーカイブのバッファーの状態を監視するのに便利です。

の`CSocketFile`使用方法の詳細については、「 [Windows ソケット:アーカイブ](../../mfc/windows-sockets-using-sockets-with-archives.md) と[Windows ソケットでのソケットの使用:アーカイブ](../../mfc/windows-sockets-example-of-sockets-using-archives.md)を使用するソケットの例。

## <a name="see-also"></a>関連項目

[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket クラス](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket クラス](../../mfc/reference/csocket-class.md)
