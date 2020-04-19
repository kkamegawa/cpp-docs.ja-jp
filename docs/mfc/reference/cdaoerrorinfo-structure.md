---
title: CDaoErrorInfo 構造体
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304234"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 構造体

`CDaoErrorInfo` 構造体には、データアクセスオブジェクト (DAO) 用に定義されたエラーオブジェクトに関する情報が含まれています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
struct CDaoErrorInfo
{
    long m_lErrorCode;
    CString m_strSource;
    CString m_strDescription;
    CString m_strHelpFile;
    long m_lHelpContext;
};
```

#### <a name="parameters"></a>パラメーター

*m_lErrorCode*<br/>
数値の DAO エラーコード。 DAO ヘルプの「トラップ可能データアクセスエラー」を参照してください。

*m_strSource*<br/>
最初にエラーを生成したオブジェクトまたはアプリケーションの名前。 Source プロパティは、最初にエラーを生成したオブジェクトを表す文字列式を指定します。式は通常、オブジェクトのクラス名です。 詳細については、DAO ヘルプの「ソースプロパティ」を参照してください。

*m_strDescription*<br/>
エラーに関連付けられている説明文字列。 詳細については、DAO ヘルプの「Description プロパティ」を参照してください。

*m_strHelpFile*<br/>
Microsoft Windows ヘルプファイルへの完全修飾パスです。 詳細については、DAO ヘルプのトピック「HelpContext、HelpFile のプロパティ」を参照してください。

*m_lHelpContext*<br/>
Microsoft Windows ヘルプファイルのトピックのコンテキスト ID。 詳細については、DAO ヘルプのトピック「HelpContext、HelpFile のプロパティ」を参照してください。

## <a name="remarks"></a>コメント

MFC では、DAO エラーオブジェクトはクラスにカプセル化されません。 代わりに、 [CDaoException](../../mfc/reference/cdaoexception-class.md)クラスには、DAO `DBEngine` オブジェクトに含まれるエラーコレクションにアクセスするためのインターフェイスが用意されています。このオブジェクトには、すべてのワークスペースも含まれます。 キャッチした `CDaoException` オブジェクトが MFC DAO 操作によってスローされると、MFC は `CDaoErrorInfo` 構造体にデータを格納し、例外オブジェクトの[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)メンバーに格納します。 (DAO を直接呼び出すことを選択した場合は、例外オブジェクトの[GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)メンバー関数を呼び出して `m_pErrorInfo`に入力する必要があります)。

DAO エラーの処理の詳細については、「[例外: データベース例外](../../mfc/exceptions-database-exceptions.md)」を参照してください。 関連情報については、DAO ヘルプの「Error オブジェクト」を参照してください。

[CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)メンバー関数によって取得された情報は `CDaoErrorInfo` 構造体に格納されます。 例外ハンドラーでキャッチした[オブジェクトから ](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)m_pErrorInfo`CDaoException` データメンバーを調べるか、または直接呼び出し中に発生した可能性のあるエラーを確認するために明示的に作成した`GetErrorInfo`オブジェクトから`CDaoException`を呼び出します。を DAO インターフェイスにします。 `CDaoErrorInfo` は、デバッグビルドで `Dump` メンバー関数も定義します。 `Dump` を使用すると、`CDaoErrorInfo` オブジェクトの内容をダンプできます。

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

## <a name="see-also"></a>参照

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException クラス](../../mfc/reference/cdaoexception-class.md)
