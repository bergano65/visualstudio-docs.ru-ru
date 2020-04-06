---
title: РегПКГ Утилита (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705636"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
> Предпочтительным способом регистрации пакетов в Visual Studio является использование файлов .pkgdef. Это позволяет развертывать расширение без доступа к реестру систем, что является обязательным условием для развертывания VSIX. Файлы Pkgdef создаются с помощью [Утилиты CreatePkgDef.](../../extensibility/internals/createpkgdef-utility.md) Для получения дополнительной информации о [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md)развертывании пакета Visual Studio см.

 Утилита RegPkg.exe регистрирует VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и готовит его к развертыванию. Эта утилита используется за кулисами во время разработки VSPackage. Он работает как часть процесса сборки, так что вы можете построить и запустить VSPackage в экспериментальном улье.

 RegPkg может генерировать сценарии системного реестра в нескольких форматах. Эти скрипты можно включить в проекты развертывания, такие как проекты .msi или файлы Windows Installer XML Toolset.

 RegPkg.exe, как \<правило, находится на *Визуальной студии SDK установки путь*>»VisualStudioIntegration»Tools-Bin-RegPkg.exe. RegPkg следует этому синтаксису:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Выполняет регистрацию под указанным

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Корневой.

 /regfile:FileName создает файл .reg вместо обновления реестра.  Не может быть использован с /vrgfile или /rgsfile или /wixfile.

 /rgsfile:FileName создает файл .rgs, а не обновляет реестр.  Не может быть использован с /vrgfile или /regfile или /wixfile.

 /vrgfile:FileName создает файл .vrg, а не обновляет реестр.  Не может быть использован с /регфилом или /rgsfile или /wixfile.

 /rgm Создает файл .rgm в дополнение к файлу rgs.  Должен быть объединен с /rgsfile.

 /wixfile:FileName создает Windows Installer XML Toolset-совместимый файл, а не обновление реестра.  Не может быть использован с /регфайл омичи или /rgsfile или /vrgfile.

 /Codebase Силы регистрации с CodeBase, а не сборки.

 /собрание сил регистрации с Ассамблеей, а не CodeBase.

 /Нерегистрируйте не регистрирует этот пакет.  Не используется

 с /регфилом или /vrgfile или /rgsfile или /wixfile.

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
- [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
