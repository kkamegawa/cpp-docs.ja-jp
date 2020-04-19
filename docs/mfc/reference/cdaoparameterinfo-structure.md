---
title: CDaoParameterInfo 構造体
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303489"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo 構造体

`CDaoParameterInfo` 構造体には、データアクセスオブジェクト (DAO) 用に定義されたパラメーターオブジェクトに関する情報が含まれています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
パラメーターオブジェクトに一意の名前を指定します。 詳細については、DAO ヘルプの「Name プロパティ」を参照してください。

*m_nType*<br/>
パラメーターオブジェクトのデータ型を示す値です。 使用可能な値の一覧については、 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)構造体の*m_nType*メンバーを参照してください。 詳細については、DAO ヘルプの「Type プロパティ」を参照してください。

*m_varValue*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md)オブジェクトに格納されているパラメーターの値。

## <a name="remarks"></a>コメント

上のプライマリとセカンダリへの参照は、`CDaoQueryDef`クラスの[Getparameterinfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)メンバー関数によって情報がどのように返されるかを示します。

MFC では、DAO パラメーターオブジェクトはクラスにカプセル化されません。 MFC `CDaoQueryDef` オブジェクトの基になる DAO querydef オブジェクトは、パラメーターコレクションにパラメーターを格納します。 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)オブジェクト内のパラメーターオブジェクトにアクセスするには、特定のパラメーター名またはインデックスをパラメーターコレクションに対して、querydef オブジェクトの `GetParameterInfo` メンバー関数を呼び出します。 [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount)メンバー関数を `GetParameterInfo` と組み合わせて使用して、Parameters コレクションをループ処理することができます。

[CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo)メンバー関数によって取得された情報は `CDaoParameterInfo` 構造体に格納されます。 パラメーターオブジェクトが格納されているパラメーターコレクションを持つ、の querydef オブジェクトの `GetParameterInfo` を呼び出します。

> [!NOTE]
>  パラメーターの値のみを取得または設定する場合は、`CDaoRecordset`クラスの[GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue)および[SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue)メンバー関数を使用します。

`CDaoParameterInfo` は、デバッグビルドで `Dump` メンバー関数も定義します。 `Dump` を使用すると、`CDaoParameterInfo` オブジェクトの内容をダンプできます。

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

## <a name="see-also"></a>参照

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)
