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
ms.openlocfilehash: e5b4e6384730492e0f34470bbe4676ce0d9012c3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310982"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
> С помощью файлах pkgdef — предпочтительный способ зарегистрировать пакеты в Visual Studio. Это позволяет расширение развертывания без доступа в системный реестр, который требуется для развертывания VSIX. Файлов pkgdef создаются с помощью [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакета Visual Studio, см. в разделе [доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Служебную программу RegPkg.exe регистрирует VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и подготавливает его для развертывания. Эта служебная программа используется скрытно, во время разработки пакета VSPackage. Он выполняется как часть процесса построения, чтобы вы можно собрать и запустить пакет VSPackage в экспериментальном кусте.

 RegPkg можно создавать скрипты реестра системы в нескольких форматах. Можно включить эти скрипты в проектах развертывания, например в проектах MSI-файл или файлы Windows Installer XML Toolset.

 RegPkg.exe обычно находится в \< *путь установки Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg придерживается следующего синтаксиса:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 регистрации выполняет /root:root под указанным

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] корневой элемент.

 /regfile:filename создает REG-файл, а не обновления реестра.  Не может использоваться с /vrgfile или /rgsfile или /wixfile.

 /rgsfile:filename создает RGS-файл, а не обновления реестра.  Не может использоваться с /vrgfile или/regfile или /wixfile.

 /vrgfile:filename создает файл .vrg вместо обновления реестра.  Не может использоваться с/regfile или /rgsfile или /wixfile.

 /rgm создает файл .rgm помимо RGS-файл.  Должны быть объединены с /rgsfile.

 /wixfile:filename создает набор инструментов Windows Installer XML-совместимый файл, а не обновления реестра.  Не может использоваться с/regfile или /rgsfile или /vrgfile.

 / codebase силы регистрации с помощью базы кода, а не сборка.

 Регистрация/Assembly силы в сборку, а не в базе кода.

 / unregister Unregisters этого пакета.  Нельзя использовать

 / regfile или /vrgfile или /rgsfile /wixfile.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
- [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)