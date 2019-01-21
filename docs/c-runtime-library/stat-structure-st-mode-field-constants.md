---
title: _stat 構造体の st_mode フィールド定数
ms.date: 11/04/2016
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
ms.openlocfilehash: 081d96fcf9b0d0d8d5183e3ed6d0fc69c5a29206
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220232"
---
# <a name="stat-structure-stmode-field-constants"></a>_stat 構造体の st_mode フィールド定数

## <a name="syntax"></a>構文

```
#include <sys/stat.h>
```

## <a name="remarks"></a>コメント

これらの定数は、[_stat 構造体](../c-runtime-library/standard-types.md)の **st_mode** フィールドでファイルの種類を示すために使用されます。

ビット マスク定数を以下に示します。

|定数|説明|
|--------------|-------------|
|`_S_IFMT`|ファイルの種類のマスク|
|`_S_IFDIR`|ディレクトリ|
|`_S_IFCHR`|特殊な文字 (設定されている場合に、デバイスを示す)|
|`_S_IFREG`|Regular|
|`_S_IREAD`|読み取りアクセス許可、所有者|
|`_S_IWRITE`|書き込みアクセス許可、所有者|
|`_S_IEXEC`|実行/検索アクセス許可、所有者|

## <a name="see-also"></a>「

[_stat、_wstat 関数](../c-runtime-library/reference/stat-functions.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[標準の型](../c-runtime-library/standard-types.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
