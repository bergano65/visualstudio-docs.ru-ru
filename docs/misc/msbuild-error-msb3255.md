---
title: "Ошибка MSBuild MSB3255 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3255
**MSB3255. Не удалось найти файлы подмножества Target Framework в каталогах Target Framework или в расположениях, указанных в InstalledAssemblySubsetTables.**  
  
 Эта ошибка происходит, когда в свойство <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A> передается имя, но найти подмножество с этим именем невозможно.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] — это подмножество полной библиотеки времени выполнения платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5.  Дополнительные сведения о веб\-службе [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] см. в разделе [Профиль клиента .NET Framework](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Процедуры  
  
### Чтобы исправить эту ошибку  
  
-   Разместите копию файла подмножества в папке требуемой версии .NET Framework или в одном из расположений, указанных в <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A>.  
  
## См. также  
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)