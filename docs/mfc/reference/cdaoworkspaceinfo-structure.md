---
title: CDaoWorkspaceInfo 構造体
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253636"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo 構造体

`CDaoWorkspaceInfo`構造体には、データ アクセス オブジェクト (DAO) のデータベース アクセスに対して定義されているワークスペースに関する情報が含まれています。

## <a name="syntax"></a>構文

```
struct CDaoWorkspaceInfo
{
    CString m_strName;           // Primary
    CString m_strUserName;       // Secondary
    BOOL m_bIsolateODBCTrans;    // All
};
```

#### <a name="parameters"></a>パラメーター

*m_strName*<br/>
Workspace オブジェクトの一意名します。 このプロパティの値を直接取得するには、クエリ定義オブジェクトを呼び出す[GetName](../../mfc/reference/cdaoquerydef-class.md#getname)メンバー関数。 詳細については、「Name プロパティ」DAO ヘルプのトピックを参照してください。

*m_strUserName*<br/>
Workspace オブジェクトの所有者を表す値。 関連情報については、「UserName プロパティ」DAO ヘルプのトピックを参照してください。

*m_bIsolateODBCTrans*<br/>
同じ ODBC データベースが関係する複数のトランザクションが分離されたかどうかを示す値。 詳細については、次を参照してください。 [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)します。 関連情報については、「IsolateODBCTrans プロパティ」DAO ヘルプのトピックを参照してください。

## <a name="remarks"></a>Remarks

クラスのオブジェクトであるワークスペース[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)します。 プライマリ、セカンダリ、および上記のすべてへの参照情報がによって返される方法を示すため、 [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)クラスのメンバー関数`CDaoWorkspace`します。

によって取得される情報、 [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)にメンバー関数が格納されている、`CDaoWorkspaceInfo`構造体。 `CDaoWorkspaceInfo` 定義、`Dump`デバッグでのメンバー関数を作成します。 使用することができます`Dump`の内容をダンプする`CDaoWorkspaceInfo`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdao.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace クラス](../../mfc/reference/cdaoworkspace-class.md)
