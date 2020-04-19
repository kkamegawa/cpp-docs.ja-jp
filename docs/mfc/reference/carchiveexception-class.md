---
title: CArchiveException クラス
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391310"
---
# <a name="carchiveexception-class"></a>CArchiveException クラス

シリアル化の例外条件を表します

## <a name="syntax"></a>構文

```
class CArchiveException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|`CArchiveException` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|例外の原因を示します。|
|[CArchiveException::m_strFileName](#m_strfilename)|この例外の状態のファイルの名前を指定します。|

## <a name="remarks"></a>Remarks

`CArchiveException`クラスには、例外の原因を示すパブリック データ メンバーが含まれています。

`CArchiveException` オブジェクトが構築され、内でスローされた[CArchive](../../mfc/reference/carchive-class.md)メンバー関数。 これらのオブジェクトのスコープ内にアクセスすることができます、**キャッチ**式。 原因のコードは、別のオペレーティング システムです。 例外処理の詳細については、次を参照してください。[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException

構築します、`CArchiveException`の値を格納するオブジェクト*原因*オブジェクト。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>パラメーター

*cause*<br/>
例外の理由を示す列挙型の変数。 列挙子の一覧は、次を参照してください。、[は](#m_cause)データ メンバー。

*lpszArchiveName*<br/>
名前を含む文字列の指す、`CArchive`例外を発生させるオブジェクト。

### <a name="remarks"></a>Remarks

作成することができます、`CArchiveException`グローバル関数をヒープ上のオブジェクトし自分でスローさせたり[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)処理を行います。

このコンス トラクターを直接使用しないでください。代わりに、グローバル関数を呼び出す`AfxThrowArchiveException`します。

##  <a name="m_cause"></a>  CArchiveException::m_cause

例外の原因を指定します。

```
int m_cause;
```

### <a name="remarks"></a>Remarks

このデータ メンバーが型のパブリック変数**int**します。その値は、`CArchiveException`列挙型。 列挙子とその意味は次のとおりです。

- `CArchiveException::none` エラーはありません。

- `CArchiveException::genericException` 指定されていないエラーです。

- `CArchiveException::readOnly` 読み込みの開かれたアーカイブに書き込もうとしました。

- `CArchiveException::endOfFile` オブジェクトの読み取り中に、数に達しましたファイルの終わりを検出します。

- `CArchiveException::writeOnly` 格納するために開かれたアーカイブから読み取ろうとしました。

- `CArchiveException::badIndex` 無効なファイル形式です。

- `CArchiveException::badClass` 無効な型のオブジェクトに、オブジェクトを読み取るしようとしています。

- `CArchiveException::badSchema` クラスの別のバージョンを持つオブジェクトを読み込もうとしました。

    > [!NOTE]
    >  これらの `CArchiveException` 原因列挙子は、`CFileException` 原因列挙子とは異なります。

    > [!NOTE]
    > `CArchiveException::generic` は使用されなくなりました。 代わりに、`genericException` を使用してください。 場合**ジェネリック**アプリケーションで使用され、ビルドは、/clr でがありますが、簡単に解読構文エラーです。

##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName

この例外の状態のファイルの名前を指定します。

```
CString m_strFileName;
```

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CArchive クラス](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[例外処理](../../mfc/reference/exception-processing.md)
