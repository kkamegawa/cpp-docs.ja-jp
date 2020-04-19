---
title: コンパイラの警告 (レベル 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388606"
---
# <a name="compiler-warning-level-1-c4055"></a>コンパイラの警告 (レベル 1) C4055

> '*変換*': データ ポインターが'*type1*'関数ポインター' に*type2*'

## <a name="remarks"></a>Remarks

**廃止されました。** Visual Studio 2017 およびそれ以降のバージョンでは、この警告は生成されません。

データポインターが、誤って関数ポインターにキャストされています。 これは /Za ではレベル 1 の警告になり、/Ze ではレベル 4 の警告になります。

## <a name="example"></a>例

次の例では C4055 が生成されます。

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

これは、/Ze ではレベル 4 の警告です。

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
