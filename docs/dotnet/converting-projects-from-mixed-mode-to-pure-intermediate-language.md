---
title: 混合モードから純粋な中間言語へのプロジェクトの変換
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 2f63b6860157e315d44f7c050812a7f0b97f2726
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448042"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>混在モードから純粋な中間言語へのプロジェクトの変換

すべてのビジュアルの C++ CLR プロジェクトは、既定では、C ランタイム ライブラリにリンクします。 その結果、ネイティブ コードと共通言語ランタイム (マネージ コード) を対象とするコードを結合するために、これらのプロジェクトは、混合モード アプリケーションとして分類されます。 コンパイル時に、中間言語 (IL) とも呼ばれる Microsoft intermediate language (MSIL) にコンパイルされます。

> [!IMPORTANT]
> Visual Studio 2015 で非推奨とされ、Visual Studio 2017 の作成をサポートできなく **/clr: 純粋な**または **/clr:safe** CLR アプリケーションのコード。 純粋なまたは安全なアセンブリを必要とする場合は、アプリケーションを c# に変換するをお勧めします。

Microsoft の以前のバージョンを使用しているかどうかはC++コンパイラ ツールセットをサポートする **/clr: 純粋な**または **/clr:safe**、コードを純粋 MSIL に変換するこの手順を使用することができます。

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>混合モード アプリケーションを純粋な中間言語に変換するには

1. リンクを削除、 [C ランタイム ライブラリ](../c-runtime-library/crt-library-features.md)(CRT)。

   1. .Cpp ファイルで、アプリケーションのエントリ ポイントを定義するへのエントリ ポイントを変更`Main()`します。 使用して`Main()`プロジェクトは、CRT にリンクしていないことを示します。

   2. ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**プロパティ**ショートカット メニューのアプリケーションのプロパティ ページを開きます。

   3. **[詳細設定]** のプロジェクト プロパティ ページ、**リンカー**を選択します、**エントリ ポイント**し、入力**Main**このフィールドにします。

   4. コンソール アプリケーションで、**システム**のプロジェクト プロパティ ページ、**リンカー**を選択、**サブシステム**フィールドを変更して**コンソール (/SUBSYSTEM:CONSOLE)** します。

      > [!NOTE]
      > に、Windows フォーム アプリケーションには、このプロパティを設定する必要はありません、**サブシステム**にフィールドが設定されている**Windows (/: WINDOWS サブシステム)** 既定で。

   5. Stdafx.h に、すべてコメント、`#include`ステートメント。 たとえば、コンソール アプリケーション: で

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       - または -

       たとえばでは Windows フォーム アプリケーション。

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Form1.cpp での Windows フォーム アプリケーションをコメント アウト用、 `#include` windows.h を参照するステートメント。 例:

      ```cpp
      // #include <windows.h>
      ```

2. Stdafx.h に、次のコードを追加します。

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. すべてのアンマネージ型を削除します。

   構造への参照にアンマネージ型を置き換える、必要に応じて、[システム](/dotnet/api/system)名前空間。 一般的なマネージ型は、次の表のとおりです。

   |構造体|説明|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|ブール値を表します。|
   |[Byte](/dotnet/api/system.byte)|8 ビット符号なし整数を表します。|
   |[Char](/dotnet/api/system.char)|Unicode 文字を表します。|
   |[DateTime](/dotnet/api/system.datetime)|通常、日付や時刻として表現される瞬間を表します。|
   |[Decimal](/dotnet/api/system.decimal)|10 進数を表します。|
   |[Double](/dotnet/api/system.double)|倍精度浮動小数点数を表します。|
   |[Guid](/dotnet/api/system.guid)|グローバル一意識別子 (GUID) を表します。|
   |[Int16](/dotnet/api/system.int16)|16 ビット符号付き整数を表します。|
   |[Int32](/dotnet/api/system.int32)|32 ビット符号付き整数を表します。|
   |[Int64](/dotnet/api/system.int64)|64 ビット符号付き整数を表します。|
   |[IntPtr](/dotnet/api/system.intptr)|ポインターまたはハンドルを表すときに使用されるプラットフォーム固有の型。|
   |[SByte](/dotnet/api/system.byte)|8 ビット符号付き整数を表します。|
   |[Single](/dotnet/api/system.single)|単精度浮動小数点数を表します。|
   |[TimeSpan](/dotnet/api/system.timespan)|時間間隔を表します。|
   |[UInt16](/dotnet/api/system.uint16)|16 ビット符号なし整数を表します。|
   |[UInt32](/dotnet/api/system.uint32)|32 ビット符号なし整数を表します。|
   |[UInt64](/dotnet/api/system.uint64)|64 ビット符号なし整数を表します。|
   |[UIntPtr](/dotnet/api/system.uintptr)|ポインターまたはハンドルを表すときに使用されるプラットフォーム固有の型。|
   |[void](/dotnet/api/system.void)|値を返さないメソッドを示しますメソッドは、void の戻り値の型。|