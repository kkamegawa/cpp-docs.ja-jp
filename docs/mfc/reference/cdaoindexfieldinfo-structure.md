---
title: CDaoIndexFieldInfo 構造体
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303669"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 構造体

`CDaoIndexFieldInfo` 構造体には、データアクセスオブジェクト (DAO) 用に定義されたインデックスフィールドオブジェクトに関する情報が含まれています。

DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
インデックスフィールドオブジェクトに一意の名前を付けます。 詳細については、DAO ヘルプの「Name プロパティ」を参照してください。

*m_bDescending*<br/>
Index オブジェクトによって定義されたインデックスの順序を示します。 順序が降順の場合は TRUE。

## <a name="remarks"></a>コメント

インデックスオブジェクトには、複数のフィールドを含めることができます。これは、テーブル (またはテーブルに基づくレコードセット) がインデックス化されているフィールドを示します。 上のプライマリへの参照は、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo)または[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)クラスの `GetIndexInfo` メンバー関数を呼び出すことによって取得される[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)オブジェクトの `m_pFieldInfos` メンバーで情報がどのように返されるかを示します。

インデックスオブジェクトとインデックスフィールドオブジェクトは、MFC クラスでは表されません。 代わりに、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)クラスまたは[CDAORECORDSET](../../mfc/reference/cdaorecordset-class.md)クラスの MFC オブジェクトの基になる DAO オブジェクトには、Indexes コレクションと呼ばれるインデックスオブジェクトのコレクションが含まれています。 各インデックスオブジェクトには、フィールドオブジェクトのコレクションが含まれています。 これらのクラスは、インデックス情報の個々の項目にアクセスするためのメンバー関数を提供します。また、親オブジェクトの `GetIndexInfo` メンバー関数を呼び出すことによって、`CDaoIndexInfo` オブジェクトを使用して一度にすべてのオブジェクトにアクセスすることもできます。 `CDaoIndexInfo` オブジェクトには、`CDaoIndexFieldInfo` オブジェクトの配列を指すデータメンバー `m_pFieldInfos`があります。

対象となるインデックスオブジェクトが格納されているインデックスのコレクションが格納されているテーブルテーブルまたはレコードセットオブジェクトの `GetIndexInfo` メンバー関数を呼び出します。 次に、 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)オブジェクトの `m_pFieldInfos` メンバーにアクセスします。 `m_pFieldInfos` 配列の長さは `m_nFields`に格納されます。 `CDaoIndexFieldInfo` は、デバッグビルドで `Dump` メンバー関数も定義します。 `Dump` を使用すると、`CDaoIndexFieldInfo` オブジェクトの内容をダンプできます。

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

## <a name="see-also"></a>参照

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset:: GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
