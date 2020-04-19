---
title: CMemFile クラス
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: a57f4e245ca1e93ec0edd454a7f407aeda5beca4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341675"
---
# <a name="cmemfile-class"></a>CMemFile クラス

[CFile](../../mfc/reference/cfile-class.md)-メモリ ファイルをサポートするクラスを派生します。

## <a name="syntax"></a>構文

```
class CMemFile : public CFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|メモリ ファイル オブジェクトを作成します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMemFile::Attach](#attach)|メモリ ブロックをアタッチします`CMemFile`します。|
|[CMemFile::Detach](#detach)|メモリ ブロックをデタッチ`CMemFile`デタッチされたメモリのブロックにポインターを返します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|メモリ割り当ての動作の変更をオーバーライドします。|
|[CMemFile::Free](#free)|オーバーライドすると、メモリの割り当て解除の動作を変更します。|
|[CMemFile::GrowFile](#growfile)|オーバーライドすると、ファイルを拡張するときの動作を変更します。|
|[CMemFile::Memcpy](#memcpy)|オーバーライドすると、ファイルを読み書きするときに、メモリ コピー動作を変更します。|
|[CMemFile::Realloc](#realloc)|メモリ再割り当ての動作の変更をオーバーライドします。|

## <a name="remarks"></a>Remarks

これらのメモリ ファイルは、ファイルがディスクではなく RAM に格納されていることを除いて、ディスク ファイルと同様に動作します。 メモリ ファイルは高速な一時ストレージまたは生バイトを転送するために役立ちます。 または、独立したプロセスの間でオブジェクトをシリアル化します。

`CMemFile` 独自のメモリ ブロックをアタッチするオブジェクトが独自のメモリを自動的に割り当てることも、`CMemFile`オブジェクトを呼び出すことによって[アタッチ](#attach)します。 いずれの場合も、メモリ ファイルを自動的に拡大するためのメモリが割り当てられている`nGrowBytes`-場合分ずつ`nGrowBytes`がゼロでないです。

メモリ ブロックの破棄後に自動的に削除されます、`CMemFile`オブジェクトで最初のメモリに割り当てられたかどうか、`CMemFile`オブジェクト。 それ以外の場合、あなたは、オブジェクトに関連付けられているメモリの割り当て解除を担当します。

切断するときに指定したポインターを通じてメモリ ブロックにアクセスすることができます、`CMemFile`オブジェクトを呼び出すことによって[デタッチ](#detach)します。

最も一般的な用途`CMemFile`を作成するには、`CMemFile`オブジェクトを呼び出すことによってこれを使用して[CFile](../../mfc/reference/cfile-class.md)メンバー関数。 作成することに注意してください、`CMemFile`それが自動的に開きます。 呼び出さないでください[CFile::Open](../../mfc/reference/cfile-class.md#open)、ディスク ファイルにのみ使用されます。 `CMemFile`ディスク ファイルのデータ メンバーを使用しない`CFile::m_hFile`は使用されません。

`CFile`メンバー関数[複製](../../mfc/reference/cfile-class.md#duplicate)、 [LockRange](../../mfc/reference/cfile-class.md#lockrange)と[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)に実装されていない`CMemFile`。 これらの関数を呼び出す場合、`CMemFile`オブジェクトの取得は、 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)します。

`CMemFile` ランタイム ライブラリ関数を使用して[malloc](../../c-runtime-library/reference/malloc.md)、 [realloc](../../c-runtime-library/reference/realloc.md)、および[無料](../../c-runtime-library/reference/free.md)割り当てるには、再割り当て、およびメモリと、組み込みの割り当てを解除[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)ブロック読み書きするときに、メモリをコピーします。 たいかどうかこの動作または動作を変更するときに`CMemFile`、ファイルの拡大からクラスを派生`CMemFile`し、適切な関数をオーバーライドします。

詳細については`CMemFile`、記事をご覧ください[MFC のファイル](../../mfc/files-in-mfc.md)と[メモリ管理 (MFC)](../../mfc/memory-management.md)して[ファイル処理](../../c-runtime-library/file-handling.md)で、*実行時ライブラリ リファレンス*します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

この関数を呼び出して`CMemFile`メンバー関数。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>パラメーター

*nBytes*<br/>
割り当てられるメモリのバイト数。

### <a name="return-value"></a>戻り値

割り当てられたメモリ ブロックへのポインターまたは NULL の場合は、割り当てに失敗しました。

### <a name="remarks"></a>Remarks

独自のメモリ割り当てを実装するには、この関数をオーバーライドします。 この関数をオーバーライドする場合はおそらくたいオーバーライド[Free](#free)と[Realloc](#realloc)もします。

既定の実装は、ランタイム ライブラリ関数を使用して[malloc](../../c-runtime-library/reference/malloc.md)メモリを割り当てることです。

##  <a name="attach"></a>  CMemFile::Attach

メモリのブロックを接続するには、この関数を呼び出す`CMemFile`します。

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>パラメーター

*lpBuffer*<br/>
接続するバッファーへのポインター`CMemFile`します。

*nBufferSize*<br/>
バッファーのサイズをバイト単位で示す整数。

*nGrowBytes*<br/>
バイトのメモリ割り当てインクリメントします。

### <a name="remarks"></a>Remarks

これにより、`CMemFile`メモリ ファイルとしてのメモリ ブロックを使用します。

場合*nGrowBytes*は 0 です。`CMemFile`にファイルの長さを設定*nBufferSize*します。 つまり、メモリ ブロック内のデータに割り当てられる前に`CMemFile`ファイルとして使用されます。 この方法で作成されたメモリ ファイルは拡張できません。

ファイルを拡張することはできません、ために発生しないように注意する`CMemFile`しようとすると、ファイルを拡張します。 たとえば、呼び出さないでください、`CMemFile`のオーバーライド[CFile:Write](../../mfc/reference/cfile-class.md#write)に末尾を越えて書き込みまたは呼び出さないでください[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)長より長く*nBufferSize*。

場合*nGrowBytes*は 0 より大きく、`CMemFile`アタッチしたメモリ ブロックの内容は無視されます。 スクラッチを使用してから、メモリ ファイルの内容を記述する必要があります、`CMemFile`のオーバーライド`CFile::Write`します。 ファイルの末尾を越えて書き込みまたは呼び出すことによって、ファイルを拡張しようとした場合、`CMemFile`のオーバーライド`CFile::SetLength`、`CMemFile`単位でメモリの割り当てが増大*nGrowBytes*します。 メモリ割り当ての成長にメモリ ブロックを渡す場合は失敗`Attach`と互換性のあるメソッドを使用して割り当てられていませんでした[アロケーション](#alloc)します。 既定の実装と互換性がある`Alloc`、ランタイム ライブラリ関数を使用したメモリを割り当てる必要があります[malloc](../../c-runtime-library/reference/malloc.md)または[calloc](../../c-runtime-library/reference/calloc.md)します。

##  <a name="cmemfile"></a>  CMemFile::CMemFile

最初のオーバー ロードは、空のメモリ ファイルを開きます。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>パラメーター

*nGrowBytes*<br/>
バイトのメモリ割り当てインクリメントします。

*lpBuffe*サイズの情報を受け取るバッファーへのポインターを r *nBufferSize*します。

*nBufferSize*<br/>
ファイル バッファーのサイズをバイト単位で示す整数。

### <a name="remarks"></a>Remarks

コンス トラクターでファイルを開くことと、呼び出す必要がありますいないことに注意してください[CFile::Open](../../mfc/reference/cfile-class.md#open)します。

最初のコンス トラクターを使用し、呼び出してすぐにした場合と同じ 2 つ目のオーバー ロードは、動作[アタッチ](#attach)同じパラメーターを使用します。 詳細については、「`Attach`」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

によって使用されているメモリ ブロックへのポインターを取得するには、この関数を呼び出す`CMemFile`します。

```
BYTE* Detach();
```

### <a name="return-value"></a>戻り値

メモリのファイルの内容を格納するメモリ ブロックへのポインター。

### <a name="remarks"></a>Remarks

閉じのこの関数を呼び出す、`CMemFile`します。 メモリ ブロックを再アタッチできます`CMemFile`呼び出して[アタッチ](#attach)します。 呼び出す必要があります、ファイルを再アタッチして、データを使用する場合は、[結び付けてその中](../../mfc/reference/cfile-class.md#getlength)呼び出す前に、ファイルの長さを取得する`Detach`します。 メモリ ブロックをアタッチする場合に注意する`CMemFile`そのデータを使用できるように ( `nGrowBytes` 0 を = =)、メモリ ファイルを拡張することはできませんし、します。

##  <a name="free"></a>  CMemFile::Free

この関数を呼び出して`CMemFile`メンバー関数。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>パラメーター

*lpMem*<br/>
解放するメモリへのポインター。

### <a name="remarks"></a>Remarks

カスタムのメモリの解放を実装するには、この関数をオーバーライドします。 この関数をオーバーライドする場合はおそらくたいオーバーライド[アロケーション](#alloc)と[Realloc](#realloc)もします。

##  <a name="growfile"></a>  CMemFile::GrowFile

この関数は、いくつかの`CMemFile`メンバー関数。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>パラメーター

*dwNewLen*<br/>
メモリ ファイルの新しいサイズ。

### <a name="remarks"></a>Remarks

変更する場合にオーバーライドできる方法`CMemFile`そのファイルを拡大します。 既定の実装[Realloc](#realloc)既存のブロックを拡張する (または[アロケーション](#alloc)メモリ ブロックを作成する) の倍数でメモリを割り当て、`nGrowBytes`コンス トラクターで指定された値または[アタッチ](#attach)呼び出します。

##  <a name="memcpy"></a>  CMemFile::Memcpy

この関数は、`CMemFile`のオーバーライド[:read](../../mfc/reference/cfile-class.md#read)と[CFile::Write](../../mfc/reference/cfile-class.md#write)とメモリ ファイルからデータを転送します。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>パラメーター

*lpMemTarget*<br/>
ソースのメモリのコピー先のメモリ ブロックへのポインター。

*lpMemSource*<br/>
ソースのメモリ ブロックへのポインター。

*nBytes*<br/>
コピー対象のバイト数。

### <a name="return-value"></a>戻り値

コピーを*lpMemTarget*します。

### <a name="remarks"></a>Remarks

方法を変更する場合は、この関数をオーバーライドする`CMemFile`はメモリをコピーします。

##  <a name="realloc"></a>  CMemFile::Realloc

この関数を呼び出して`CMemFile`メンバー関数。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>パラメーター

*lpMem*<br/>
再割り当てするメモリ ブロックへのポインター。

*nBytes*<br/>
メモリ ブロックの新しいサイズ。

### <a name="return-value"></a>戻り値

再割り当て (および移動した可能性があります)、メモリ ブロックへのポインター、再割り当てが失敗した場合は null です。

### <a name="remarks"></a>Remarks

カスタムのメモリを再割り当てを実装するには、この関数をオーバーライドします。 この関数をオーバーライドする場合はおそらくたいオーバーライド[アロケーション](#alloc)と[Free](#free)もします。

## <a name="see-also"></a>関連項目

[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
