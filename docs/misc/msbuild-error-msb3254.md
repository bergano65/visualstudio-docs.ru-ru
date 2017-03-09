---
title: "Ошибка MSBuild MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3254
**MSB3254. Файл \<имя\> будет проигнорирован, так как его невозможно прочитать.  Этот файл передан в InstalledAssemblySubsetTables или найден в папке \<имя\> в TargetFrameworkDirectories.**  
  
 Эта ошибка происходит, когда невозможно прочитать XML\-файл [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], client.xml.  Файл не читается из\-за повреждения, блокировки или некоторой другой проблемы.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] — это подмножество полной библиотеки времени выполнения платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5.  Дополнительные сведения о веб\-службе [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] см. в разделе [Профиль клиента .NET Framework](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Процедуры  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь в наличии всех прав и полного доступа к файлу или переустановите распространяемую библиотеку времени выполнения [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], чтобы заменить поврежденный файл.  
  
## См. также  
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)