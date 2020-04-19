---
title: /DEBUGTYPE (デバッグ情報オプション)
ms.date: 11/04/2016
f1_keywords:
- /debugtype
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
ms.openlocfilehash: 00e3cb61f8ec9aa707bb72aa9ff05a64f98d4e47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272296"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (デバッグ情報オプション)

/DEBUGTYPE オプションは、/DEBUG オプションによって生成されるデバッグ情報の種類を指定します。

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>引数

**CV**<br/>
シンボル、行番号、その他のオブジェクトのコンパイル情報のデバッグ情報を PDB ファイルに出力するようにリンカーに指示します。 既定では、このオプションが有効になっているときに **/debug**が指定されて、 **/DEBUGTYPE**が指定されていません。

**PDATA**<br/>
.pdata エントリと .xdata エントリを PDB ファイル内のデバッグ ストリーム情報に追加するようにリンカーに指示します。 既定では、このオプションが有効になっているときに両方、 **/debug**と **/DRIVER**オプションを指定します。 場合 **/DEBUGTYPE:PDATA**リンカーが自動的にデバッグ シンボルを PDB ファイルを含む、自体によって指定されます。 場合 **/DEBUGTYPE:PDATA、フィックス アップ**指定すると、リンカーはデバッグ シンボルを PDB ファイルに含まれません。

**フィックス アップ**<br/>
再配置テーブル エントリを PDB ファイル内のデバッグ ストリーム情報に追加するようにリンカーに指示します。 既定では、このオプションが有効になっているときに両方、 **/debug**と **/profile**オプションを指定します。 場合 **/DEBUGTYPE:FIXUP**または **/DEBUGTYPE:FIXUP、PDATA**指定すると、リンカーはデバッグ シンボルを PDB ファイルに含まれません。

引数を **/DEBUGTYPE**をコンマで区切ることによって任意の順序で組み合わせることができます。 **/DEBUGTYPE**オプションとその引数は大文字小文字が区別されません。

## <a name="remarks"></a>Remarks

使用して、 **/DEBUGTYPE**デバッグ ストリームで再配置テーブル データまたは .pdata および .xdata ヘッダー情報を含めることを指定するオプション。 これにより、リンカーは、カーネルモード コードで中断するときにカーネル デバッガーに表示されるユーザーモード コードに関する情報を含めます。 ときにデバッグ シンボルを使用できるようにする**FIXUP**が指定すると、含める、 **CV**引数。

アプリケーションの一般的なものは、ユーザー モードでコードをデバッグする、 **/DEBUGTYPE**オプションは必要ありません。 既定では、デバッグを指定するコンパイラ スイッチが出力 ([/Z7、/Zi、/ZI](z7-zi-zi-debug-information-format.md)) すべてについては、必要な Visual Studio でデバッガーの出力します。 使用 **/DEBUGTYPE:PDATA**または **/DEBUGTYPE:CV, PDATA、FIXUP**デバイス ドライバーの構成アプリなど、ユーザー モードおよびカーネル モードのコンポーネントを組み合わせてするコードをデバッグします。 カーネル モード デバッガーの詳細については、次を参照してください[デバッグ ツールの Windows (WinDbg、KD、CDB、NTSD)。](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>関連項目

[/DEBUG (デバッグ情報の生成)](debug-generate-debug-info.md)<br/>
[/DRIVER (Windows NT カーネル モード ドライバー)](driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (パフォーマンス ツール プロファイラー)](profile-performance-tools-profiler.md)<br/>
[(WinDbg、KD、CDB、NTSD)、Windows 用デバッグ ツール](/windows-hardware/drivers/debugger/index)
