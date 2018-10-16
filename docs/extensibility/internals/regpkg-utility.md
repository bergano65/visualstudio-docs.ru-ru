---
title: Служебная программа RegPkg | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130959"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
>  С помощью файлов .pkgdef — предпочтительный способ регистрации пакетов в Visual Studio. Это обеспечивает расширение развертывания без необходимости доступа к реестру системы, что является требованием для развертывания VSIX. Pkgdef файлы создаются с помощью [CreatePkgDef программы](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакета Visual Studio см. в разделе [доставки расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Служебную программу RegPkg.exe регистрирует VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и подготавливает его для развертывания. Эта программа используется скрытно, во время разработки пакета VSPackage. Он выполняется как часть процесса построения, чтобы можно было создавать и запустите VSPackage в экспериментальном кусте.  
  
 RegPkg можно создавать скрипты реестра системы в нескольких форматах. Вы можете включить эти скрипты в проекты развертывания, такие как проекты MSI-файл или файлы Windows Installer XML Toolset.  
  
 RegPkg.exe обычно находится в \< *путь установки Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg имеет следующий синтаксис:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Выполняет регистрацию под указанным  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] корневой элемент.  
  
 /regfile:filename  
 Создает REG-файл, а не обновление реестра.  Не может использоваться с /vrgfile или /rgsfile или /wixfile.  
  
 /rgsfile:filename  
 Создает RGS-файл, а не обновление реестра.  Не может использоваться с /vrgfile или/regfile или /wixfile.  
  
 /vrgfile:filename  
 Создает vrg-файла, а не обновление реестра.  Нельзя использовать с/regfile или /rgsfile или /wixfile.  
  
 /rgm  
 Создает файл .rgm помимо RGS-файл.  Должны быть объединены с /rgsfile.  
  
 /wixfile:filename  
 Создает файл совместимый набор инструментов Windows Installer XML вместо обновления реестра.  Нельзя использовать с/regfile или /rgsfile или /vrgfile.  
  
 /codebase  
 Регистрация принудительно с помощью базы кода, а не сборка.  
  
 / Assembly  
 Принудительная регистрация в сборку, а не на базе кода.  
  
 / unregister  
 Отменяет регистрацию этого пакета.  Нельзя использовать  
  
 / regfile /vrgfile или /rgsfile или /wixfile.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)  
 [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)