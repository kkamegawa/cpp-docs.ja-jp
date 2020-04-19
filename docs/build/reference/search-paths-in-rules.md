---
title: 規則の検索パス
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: eab6e9d32940aaf5729ce82c4e8258a3a3132208
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318863"
---
# <a name="search-paths-in-rules"></a>規則の検索パス

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Remarks

依存関係で正確に指定されたパスの推論規則のパスを一致する場合にのみ依存関係を推論規則が適用されます。 依存ファイルのディレクトリを指定する*frompath*とターゲットのディレクトリで*topath*; スペースは使用できません。 各拡張機能の 1 つだけのパスを指定します。 拡張機能の 1 つ上のパスには、別のパスが必要です。 現在のディレクトリを指定するには、ピリオド (.) または空のかっこ ({}) のいずれかを使用します。 マクロが表すことができます*frompath*と*topath*; プリプロセス時に呼び出されます。

## <a name="example"></a>例

### <a name="code"></a>コード

```
{dbi\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUDBI) $<

{ilstore\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{misc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{misc\}.c{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{msf\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{bsc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{mre\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{namesrvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{src\cvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<
```

## <a name="see-also"></a>関連項目

[規則の定義](defining-a-rule.md)
