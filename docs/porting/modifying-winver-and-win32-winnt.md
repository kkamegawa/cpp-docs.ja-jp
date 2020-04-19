---
title: WINVER および _WIN32_WINNT の更新
description: アップグレードされた Visual Studio C++プロジェクトで WINVER と _WIN32_WINNT マクロを更新するタイミングと方法。
ms.date: 01/22/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: b81c7967732c7b0c23ff0eb73d2a866a9b33713b
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725697"
---
# <a name="update-winver-and-_win32_winnt"></a>WINVER および _WIN32_WINNT の更新

Windows SDK を使用する場合は、コードを実行できる Windows のバージョンを指定できます。 プリプロセッサマクロ**WINVER**と **_WIN32_WINNT**は、コードがサポートするオペレーティングシステムの最小バージョンを指定します。 Visual Studio と Microsoft C++コンパイラは、WINDOWS 7 SP1 以降を対象としています。 以前のツールセットには、Windows XP SP4、Windows Server 2003 SP4、Vista、および Windows Server 2008 のサポートが含まれています。 Windows 95、Windows 98、Windows ME、Windows NT、および Windows 2000 はサポートされていません。

古いプロジェクトをアップグレードするときに、 **WINVER**または **_WIN32_WINNT**マクロを更新することが必要になる場合があります。 サポートされていないバージョンの Windows に対して値が割り当てられている場合は、これらのマクロに関連するコンパイルエラーが発生する可能性があります。

## <a name="remarks"></a>コメント

マクロを変更するには、ヘッダーファイル (たとえば、Windows を対象とするいくつかのプロジェクトテンプレートに含まれる*targetver*) で、次の行を追加します。

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

この例のマクロは、Windows 10 オペレーティングシステムのすべてのバージョンを対象とするように設定されています。 使用可能な値は、Windows ヘッダーファイル sdkddkver.h に一覧表示されます。このファイルは、主要な Windows バージョンごとにマクロを定義し*ます*。 以前の Windows プラットフォームをサポートするアプリケーションをビルドするには、 *winsdkver.h インクルード*をインクルードします。 次に、 *sdkddkver.h*を含める前に、 **WINVER**と **_WIN32_WINNT**マクロを、サポートされている最も古いプラットフォームに設定します。 Windows のメジャーバージョンごとに値をエンコードする*sdkddkver.h*の WINDOWS 10 SDK バージョンの行を次に示します。

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

バージョン管理の詳細な方法については、 *sdkddkver.h*の NTDDI version 定数を使用できます。 Windows 10 SDK バージョン10.0.18362.0 の*sdkddkver.h*で定義されているマクロの一部を次に示します。

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

**Osver**マクロ、 **spver**マクロ、および**subver**マクロをコード内で使用して、さまざまなレベルの API サポートの条件付きコンパイルを制御できます。

*Sdkddkver.h*に表示されているすべてのバージョンの Windows が表示されない場合があります。 つまり、古いバージョンの Windows SDK が使用されていることがあります。 既定では、Visual Studio の新しい Windows プロジェクトは Windows 10 SDK を使用します。

> [!NOTE]
> アプリケーションに内部 MFC ヘッダーを含めた場合には、値が動作する保証はありません。

`/D` コンパイラ オプションを使用して、このマクロを定義することもできます。 詳細については、「 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)」を参照してください。

これらのマクロの意味について詳しくは、「 [Windows ヘッダーの使用](/windows/win32/WinProg/using-the-windows-headers)」をご覧ください。

## <a name="see-also"></a>関連項目

[Visual C++ の変更履歴](../porting/visual-cpp-change-history-2003-2015.md)
