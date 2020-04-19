---
title: CSharedFile クラス
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502612"
---
# <a name="csharedfile-class"></a>CSharedFile クラス

共有メモリファイルをサポートする[CMemFile](../../mfc/reference/cmemfile-class.md)の派生クラス。

## <a name="syntax"></a>構文

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|`CSharedFile` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|共有メモリファイルを閉じ、そのメモリブロックのハンドルを返します。|
|[CSharedFile:: SetHandle](#sethandle)|共有メモリファイルをメモリブロックにアタッチします。|

## <a name="remarks"></a>Remarks

メモリファイルは、ディスクファイルのように動作します。 違いは、メモリファイルがディスク上ではなく RAM に格納されていることです。 メモリファイルは、高速一時ストレージ、または生バイトまたはシリアル化されたオブジェクトを独立したプロセス間で転送する場合に役立ちます。

共有メモリファイルは、そのメモリ内の他のメモリファイルとは異なり、 [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 関数で割り当てられます。 クラス`CSharedFile`は、を使用して`GlobalAlloc`作成されたグローバルに割り当てられたメモリブロックにデータを格納します。このメモリブロックは、を使用`IDataObject`するなど、DDE、クリップボード、またはその他の OLE/COM の一様なデータ転送操作を使用して共有できます。

`GlobalAlloc`[malloc](../../c-runtime-library/reference/malloc.md)によって返されたポインターなど、メモリへのポインターではなく、HGLOBAL ハンドルを返します。 特定のアプリケーションでは、HGLOBAL ハンドルが必要です。 たとえば、クリップボードにデータを格納するには、HGLOBAL ハンドルが必要です。

`CSharedFile`では、メモリマップトファイルを使用せず、プロセス間でデータを直接共有することはできません。

`CSharedFile`オブジェクトは、独自のメモリを自動的に割り当てることができます。 または、 [csharedfile:: SetHandle](#sethandle)を呼び出し`CSharedFile`て、オブジェクトに独自のメモリブロックをアタッチすることもできます。 どちらの場合も、メモリファイルを自動的に拡張するための`nGrowBytes`メモリは、が`nGrowBytes` 0 でない場合、サイズの増加した単位で割り当てられます。

詳細については、「 [MFC のファイル](../../mfc/files-in-mfc.md)」と「*ランタイムライブラリリファレンス*」の「[ファイル処理](../../c-runtime-library/file-handling.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxadv

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

`CSharedFile`オブジェクトを構築し、そのオブジェクトにメモリを割り当てます。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>パラメーター

*nAllocFlags*<br/>
メモリを割り当てる方法を示すフラグ。 有効なフラグ値の一覧については、「 [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) 」を参照してください。

*nGrowBytes*<br/>
メモリ割り当ての増分値 (バイト単位)。

##  <a name="detach"></a>  CSharedFile::Detach

メモリファイルを閉じてメモリブロックからデタッチするには、この関数を呼び出します。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>戻り値

メモリファイルの内容を格納しているメモリブロックのハンドル。

### <a name="remarks"></a>Remarks

**Detach**によって返されたハンドルを使用して[SetHandle](#sethandle)を呼び出すことで、再度開くことができます。

##  <a name="sethandle"></a>  CSharedFile::SetHandle

グローバルメモリのブロックを`CSharedFile`オブジェクトにアタッチするには、この関数を呼び出します。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>パラメーター

*hGlobalMemory*<br/>
にアタッチするグローバルメモリへのハンドル`CSharedFile`。

*bAllowGrow*<br/>
メモリブロックの拡張を許可するかどうかを指定します。

### <a name="remarks"></a>Remarks

*Ballowgrow*が0以外の場合は、メモリブロックのサイズよりも多くのバイトをファイルに書き込もうとするなど、必要に応じてメモリブロックのサイズが増加します。

## <a name="see-also"></a>関連項目

[CMemFile クラス](../../mfc/reference/cmemfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMemFile クラス](../../mfc/reference/cmemfile-class.md)
