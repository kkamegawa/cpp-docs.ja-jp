---
title: ストアド プロシージャの定義
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 0f4c4ad84abf2a5de2cdf09e7064396ea01eeebe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176396"
---
# <a name="defining-stored-procedures"></a>ストアド プロシージャの定義

ストアド プロシージャを呼び出す前に最初に定義してそれを使用して、 [DEFINE_COMMAND](../../data/oledb/define-command.md)マクロ。 コマンドを定義するときに、パラメーター マーカーとして疑問符 (?) でパラメーターを表します。

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

このトピックのコード例で使用される構文 (中かっこの使用) は、SQL Server に固有です。 使用するプロバイダーに応じて、ストアド プロシージャで使用する構文が異なる場合があります。

次に、パラメーターのマップでは、コマンドで出現する順序でパラメーターを一覧表示コマンドで使用するパラメーターを指定します。

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

前の例が移動するときに、ストアド プロシージャを定義します。 通常、コードを効率的に再利用のデータベースのセットを含む名前を持つ定義済みのストアド プロシージャなど`Sales by Year`または`dt_adduserobject`します。 SQL Server Enterprise Manager を使用してその定義を表示することができます。 次のように呼び出します (の配置、*でしょうか。* パラメーターに依存、ストアド プロシージャのインターフェイス)。

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

次に、コマンド クラスを宣言します。

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

最後、ストアド プロシージャを呼び出す`OpenRowset`次のようにします。

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

またデータベース属性を使用してストアド プロシージャを定義できることに注意してください[db_command](../../windows/db-command.md)次のようにします。

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>関連項目

[ストアド プロシージャの使用](../../data/oledb/using-stored-procedures.md)