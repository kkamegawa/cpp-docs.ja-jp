---
title: 定義済み規則
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319448"
---
# <a name="predefined-rules"></a>定義済み規則

組み込み推論規則では、NMAKE のコマンド マクロおよびオプション マクロが使用されます。

|ルール|コマンド|既定値<br /><br /> アクション|Batch<br /><br /> ルール|nmake が実行されるプラットフォーム|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Ｘ|x86|
|.asm.obj|$(AS) $(AFLAGS)/c $<|ml/c $<|可|x86|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Ｘ|X64|
|.asm.obj|$(AS) $(AFLAGS)/c $<|ml64/c $<|可|X64|
|.c.exe|$ (CC) $(CFLAGS) $&LT;|cl $<|Ｘ|all|
|.c.obj|$ (Cc) $(CFLAGS)/c $<|cl/c $<|可|all|
|.cc.exe|$ (CC) $(CFLAGS) $&LT;|cl $<|Ｘ|all|
|.cc.obj|$ (Cc) $(CFLAGS)/c $<|cl/c $<|可|all|
|.cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|Ｘ|all|
|.cpp.obj|$(CPP) $(CPPFLAGS)/c $<|cl/c $<|可|all|
|.cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|Ｘ|all|
|.cxx.obj|$(CXX) $(CXXFLAGS)/c $<|cl/c $<|可|all|
|.rc.res|$(RC) $(RFLAGS)/r $<|rc/r $<|Ｘ|all|

## <a name="see-also"></a>関連項目

[推論規則](inference-rules.md)
