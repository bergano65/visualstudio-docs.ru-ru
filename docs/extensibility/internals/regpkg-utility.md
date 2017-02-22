---
title: "Служебная программа RegPkg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg программа регистрации"
  - "Регистрация программы regpkg"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Служебная программа RegPkg
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  С помощью файлов .pkgdef — предпочтительный способ регистрации пакетов в Visual Studio. Это позволяет для развертывания расширения, не имея доступа к системного реестра, который является обязательным для развертывания VSIX. Pkgdef файлы создаются с помощью [Служебная программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакета Visual Studio см. в разделе [Расширения Visual Studio доставки](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Программа RegPkg.exe регистрирует VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и подготавливает его для развертывания. Эта служебная программа используется в фоновом режиме во время разработки VSPackage. Он выполняется как часть процесса построения, можно построить и запустить в экспериментальном кусте VSPackage.  
  
 RegPkg можно создавать скрипты реестра системы в нескольких форматах. Можно включить эти сценарии в проектах развертывания, таких как проекты MSI\-файл или файлы Windows Installer XML Toolset.  
  
 RegPkg.exe обычно находится в \<*путь установки Visual Studio SDK*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe. RegPkg придерживается следующего синтаксиса:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 Выполняет регистрацию указанного  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] корневой элемент.  
  
 \/regfile:filename  
 Создает REG\-файл, а не обновление реестра.  Не может использоваться с \/vrgfile или \/rgsfile или \/wixfile.  
  
 \/rgsfile:filename  
 Создает RGS\-файл, а не обновление реестра.  Нельзя использовать с \/vrgfile\/regfile или \/wixfile.  
  
 \/vrgfile:filename  
 Создает файл .vrg вместо обновления реестра.  Нельзя использовать с\/regfile или \/rgsfile или \/wixfile.  
  
 \/rgm  
 Создает файл .rgm помимо RGS\-файл.  Должен использоваться вместе с \/rgsfile.  
  
 \/wixfile:filename  
 Создает файл Windows Installer XML Toolset совместимой вместо обновления реестра.  Нельзя использовать с\/regfile или \/rgsfile или \/vrgfile.  
  
 \/codebase  
 Принудительно регистрацию с помощью базы кода, а не сборка.  
  
 \/ Assembly  
 Принудительно регистрацию сборки, а не на базе кода.  
  
 \/ unregister  
 Отменяет регистрацию этого пакета.  Нельзя использовать  
  
 \/ regfile \/vrgfile или \/rgsfile или \/wixfile.  
  
## См. также  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Устранение неполадок регистрация пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)