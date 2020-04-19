---
title: CDaoRelationFieldInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: 85dd853a9aae41a87bbe7ef5c69e22846678cf8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206109"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 構造体

`CDaoRelationFieldInfo`構造体には、データ アクセス オブジェクト (DAO) に対して定義されているリレーションシップでフィールドに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
リレーションシップの主テーブル内のフィールドの名前。

*m_strForeignName*<br/>
リレーションシップの外部テーブルのフィールドの名前。

## <a name="remarks"></a>Remarks

DAO のリレーションシップ オブジェクトでは、主テーブルとリレーションシップを定義した外部テーブル内のフィールドのフィールドを指定します。 上記の構造体の定義でプライマリへの参照で、情報を返す方法を示すため、`m_pFieldInfos`のメンバー、 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)オブジェクトを呼び出すことによって取得、 [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)クラスのメンバー関数`CDaoDatabase`します。

リレーションシップ オブジェクトとフィールド オブジェクトの関係は、MFC クラスでは表されません。 DAO オブジェクトを基になる MFC オブジェクト クラスの代わりに、 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)関係コレクションと呼ばれる、関連オブジェクトのコレクションを含めることができます。 各リレーションシップ オブジェクトには、さらに、リレーションシップのフィールド オブジェクトのコレクションが含まれています。 各リレーションシップのフィールド オブジェクトは、外部テーブル内のフィールドに、主テーブル内のフィールドを関連付けます。 これらをまとめると、フィールド オブジェクトの関係を定義フィールドのグループ、各テーブルのリレーションシップを定義します。 `CDaoDatabase` リレーションシップ オブジェクトにアクセスすることができます、`CDaoRelationInfo`オブジェクトを呼び出すことによって、`GetRelationInfo`メンバー関数。 `CDaoRelationInfo`オブジェクトを持つデータ メンバー、`m_pFieldInfos`の配列を指す`CDaoRelationFieldInfo`オブジェクト。

呼び出す、 [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)含むのメンバー関数`CDaoDatabase`関係コレクションが格納興味のあるリレーションシップ オブジェクトのオブジェクトします。 アクセスし、`m_pFieldInfos`のメンバー、 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)オブジェクト。 `CDaoRelationFieldInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoRelationFieldInfo`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo 構造体](../../mfc/reference/cdaorelationinfo-structure.md)
