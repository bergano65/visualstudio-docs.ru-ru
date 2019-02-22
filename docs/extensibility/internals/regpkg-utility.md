---
title: Служебная программа RegPkg | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b9b07bc801e687da9ce93968dbac59966328484
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619242"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
>  С помощью файлах pkgdef — предпочтительный способ зарегистрировать пакеты в Visual Studio. Это позволяет расширение развертывания без доступа в системный реестр, который требуется для развертывания VSIX. Файлов pkgdef создаются с помощью [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакета Visual Studio, см. в разделе [доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

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