---
title: Служебная программа RegPkg | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724447"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру, что является требованием для развертывания VSIX. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакетов Visual Studio см. в разделе [Доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Служебная программа RegPkg. exe регистрирует пакет VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и готовит его к развертыванию. Эта служебная программа используется в фоновом режиме во время разработки VSPackage. Он выполняется как часть процесса сборки, чтобы вы могли создать и запустить VSPackage в экспериментальном Hive.

 RegPkg может создавать сценарии системного реестра в нескольких форматах. Эти скрипты можно включить в проекты развертывания, такие как MSI-проекты или установщик Windows файлы набора инструментов XML.

 RegPkg. exe обычно находится в каталоге \<*установки пакета SDK для Visual Studio*> \висуалстудиоинтегратион\тулс\бин\регпкг.ЕКСЕ. RegPkg соответствует этому синтаксису:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: root выполняет регистрацию в указанном

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] корень.

 /regfile: FileName создает reg-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/ргсфиле или/виксфиле.

 /ргсфиле: FileName создает RGS-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/regfile или/виксфиле.

 /вргфиле: FileName создает ВРГ-файл, а не обновляет реестр.  Нельзя использовать с/regfile или/ргсфиле или/виксфиле.

 /РГМ создает РГМ-файл в дополнение к RGS-файлу.  Необходимо сочетать с/ргсфиле.

 /виксфиле: FileName создает файл, совместимый с набором инструментов установщик Windows XML, вместо обновления реестра.  Нельзя использовать с/regfile или/ргсфиле или/вргфиле.

 /CodeBase принудительно выполняет регистрацию с использованием базы кода, а не сборки.

 /Assembly принудительно выполняет регистрацию с помощью сборки, а не базы кода.

 /Unregister отменяет регистрацию этого пакета.  Не может использоваться

 с/regfile или/вргфиле или/ргсфиле или/виксфиле.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
- [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)