---
title: CStringT によるメモリ管理
ms.date: 11/04/2016
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: 8f83b088becf97ca3d8779a537e42369b4a8c832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235199"
---
# <a name="memory-management-with-cstringt"></a>CStringT によるメモリ管理

クラス[CStringT](../atl-mfc-shared/reference/cstringt-class.md)可変長文字列の操作に使用されるテンプレート クラスです。 これらの文字列を保持するためにメモリが割り当てられの各インスタンスに関連付けられている文字列のマネージャー オブジェクトを介してリリースされる`CStringT`します。 MFC と ATL の既定のインスタンス化を提供します。`CStringT`という`CString`、 `CStringA`、および`CStringW`、異なる文字の種類の文字列を操作します。 これらの文字型は、TCHAR 型**char**、および`wchar_t`、それぞれします。 これらの既定の文字列型では、(ATL) でプロセス ヒープまたは (MFC) では、CRT ヒープからメモリを割り当てる文字列のマネージャーを使用します。 一般的なアプリケーションは、このメモリの割り当て方法で十分です。 ただし、処理を要するコードの文字列 (マルチ スレッド コード) の既定のメモリ マネージャーが適切に機能しない可能性がありますを使用します。 このトピックでは、既定のメモリ管理動作をオーバーライドする方法を説明します`CStringT`、手元のタスク用に最適化されたアロケーターを具体的には作成します。

- [カスタム文字列マネージャーの実装 (基本方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [ヒープ競合の回避](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [カスタム文字列マネージャーの実装 (詳細方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: カスタム文字列マネージャーの例](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>関連項目

[CustomString サンプル](../overview/visual-cpp-samples.md)
