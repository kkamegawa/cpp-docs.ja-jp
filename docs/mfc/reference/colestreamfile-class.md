---
title: COleStreamFile クラス
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503687"
---
# <a name="colestreamfile-class"></a>COleStreamFile クラス

OLE の構造化記憶の一部として、複合ファイルのデータ ストリーム (`IStream`) を表します。

## <a name="syntax"></a>構文

```
class COleStreamFile : public CFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|`COleStreamFile` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleStreamFile:: Attach](#attach)|ストリームをオブジェクトに関連付けます。|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|グローバルメモリからストリームを作成し、オブジェクトに関連付けます。|
|[COleStreamFile:: CreateStream](#createstream)|ストリームを作成し、オブジェクトに関連付けます。|
|[COleStreamFile::D etach](#detach)|オブジェクトからストリームの関連付けを解除します。|
|[COleStreamFile:: System.resources.resourcemanager.getstream](#getstream)|現在のストリームを返します。|
|[COleStreamFile:: OpenStream](#openstream)|安全にストリームを開き、オブジェクトに関連付けます。|

## <a name="remarks"></a>Remarks

`IStorage`オブジェクトは、メモリストリームでない限り、ストリームを開く、または作成する前に存在している必要があります。

`COleStreamFile`オブジェクトは、 [CFile](../../mfc/reference/cfile-class.md)オブジェクトとまったく同じように操作されます。

ストリームとストレージの操作の詳細については、 [次の記事を参照してください。複合ファイル](../../mfc/containers-compound-files.md)..

詳細については、Windows SDK の「 [IStream](/windows/win32/api/objidl/nn-objidl-istream)と[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="attach"></a>COleStreamFile:: Attach

指定された OLE ストリームを`COleStreamFile`オブジェクトに関連付けます。

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>パラメーター

*lpStream*<br/>
オブジェクトに関連付けられる`IStream`OLE ストリーム () をポイントします。 Nll は指定できません。

### <a name="remarks"></a>Remarks

オブジェクトは、OLE ストリームに既に関連付けられていないことが必要です。

詳細については、Windows SDK の「 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 」を参照してください。

##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile

`COleStreamFile` オブジェクトを作成します。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>パラメーター

*lpStream*<br/>
オブジェクトに関連付けられる OLE ストリームへのポインター。

### <a name="remarks"></a>Remarks

*Lpstream*が NULL の場合、オブジェクトは ole ストリームに関連付けられません。それ以外の場合は、オブジェクトが、指定された ole ストリームに関連付けられます。

詳細については、Windows SDK の「 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 」を参照してください。

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

グローバルな共有メモリから新しいストリームを安全に作成します。障害が通常の予期される条件になります。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*pError*<br/>
作成操作の完了ステータスを示す[CFileException](../../mfc/reference/cfileexception-class.md)オブジェクトまたは NULL を指します。 ストリームを作成しようとして生成される可能性のある例外を監視する場合は、このパラメーターを指定します。

### <a name="return-value"></a>戻り値

ストリームが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

メモリは、OLE サブシステムによって割り当てられます。

詳細については、Windows SDK の「 [Createstreamonhglobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) 」を参照してください。

##  <a name="createstream"></a>COleStreamFile:: CreateStream

指定されたストレージオブジェクトに新しいストリームを安全に作成します。エラーは通常の予期される条件です。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*lpStorage*<br/>
作成するストリームが格納されている OLE ストレージオブジェクトを指します。 Nll は指定できません。

*lpszStreamName*<br/>
作成されるストリームの名前。 Nll は指定できません。

*Noペンフラグ*<br/>
ストリームを開くときに使用するアクセスモード。 既定では、排他、読み取り/書き込み、および作成の各モードが使用されます。 使用可能なモードの完全な一覧については、「 [cfile:: cfile](../../mfc/reference/cfile-class.md#cfile)」を参照してください。

*pError*<br/>
[CFileException](../../mfc/reference/cfileexception-class.md)オブジェクトまたは NULL を指します。 ストリームを作成しようとして生成される可能性のある例外を監視する場合は、このパラメーターを指定します。

### <a name="return-value"></a>戻り値

ストリームが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

Open が失敗し、エラーが NULL でない場合 、ファイル例外がスローされます。

詳細については、Windows SDK の「 [IStorage:: CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) 」を参照してください。

##  <a name="detach"></a>COleStreamFile::D etach

ストリームを閉じずに、オブジェクトからストリームの関連付けを解除します。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられ`IStream`たストリーム () へのポインター。

### <a name="remarks"></a>Remarks

ストリームは、プログラムが終了する前に、他の方法で閉じる必要があります。

詳細については、Windows SDK の「 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 」を参照してください。

##  <a name="getstream"></a>COleStreamFile:: System.resources.resourcemanager.getstream

現在のストリームへのポインターを返すには、この関数を呼び出します。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>戻り値

現在のストリームインターフェイス ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) へのポインター。

##  <a name="openstream"></a>COleStreamFile:: OpenStream

既存のストリームを開きます。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*lpStorage*<br/>
開くストリームが格納されている OLE ストレージオブジェクトを指します。 Nll は指定できません。

*lpszStreamName*<br/>
開くストリームの名前。 Nll は指定できません。

*Noペンフラグ*<br/>
ストリームを開くときに使用するアクセスモード。 既定では、排他モードと読み取り/書き込みモードが使用されます。 使用可能なモードの完全な一覧については、「 [cfile:: cfile](../../mfc/reference/cfile-class.md#cfile)」を参照してください。

*pError*<br/>
[CFileException](../../mfc/reference/cfileexception-class.md)オブジェクトまたは NULL を指します。 ストリームを開こうとして生成される可能性のある例外を監視する場合は、このパラメーターを指定します。

### <a name="return-value"></a>戻り値

ストリームが正常に開かれた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

Open が失敗し、エラーが NULL でない場合 、ファイル例外がスローされます。

詳細については、Windows SDK の「 [IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) 」を参照してください。

## <a name="see-also"></a>関連項目

[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
