---
title: "Практическое руководство: принудительная загрузка VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты VSPackage, принудительная загрузка"
  - "пакеты VSPackage, загрузка"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Практическое руководство: принудительная загрузка VSPackage
VSPackages обычно загружается только в тех случаях, когда требуется выполняет их соответствующие функции процесс.  В некоторых случаях, однако VSPackage может заставить другой VSPackage.  Например, легковес VSPackage может загрузить большее VSPackage в контексте программирования, не доступен как CMDUIContext.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> метод принудительного VSPackage для загрузки.  
  
### Принудительно для загрузки VSPackage  
  
-   Вставьте этот код <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод VSPackage, обеспечивающее другое VSPackage для загрузки:  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     После инициализации оно требует VSPackage `PackageToBeLoaded` загрузить.  
  
## Отказоустойчивость  
 Загрузка усилий не должна использоваться для взаимодействия VSPackage.  Взамен рекомендуется использовать [Использование и предоставления услуг](../extensibility/using-and-providing-services.md).  
  
## См. также  
 [Управление пакеты VSPackage](../extensibility/managing-vspackages.md)   
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)