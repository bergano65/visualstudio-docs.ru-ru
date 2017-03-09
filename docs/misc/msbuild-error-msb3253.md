---
title: "Ошибка MSBuild MSB3253 | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3253
**MSB3254. Сборка \<имя\>, на которую имеется ссылка в проекте, зависит от сборки \<имя 2\>, отсутствующей в клиентском профиле платформы .NET Framework.**  
  
 Одна из сборок \(или зависимых сборок\), на которую есть ссылка в проекте, зависит от другой сборки, отсутствующей в подмножестве [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 Это сообщение обычно появляется, когда в проекте имеется ссылка на сторонний элемент управления или библиотеку DLL, где есть ссылка на внешнюю сборку.  Например, в проекте используется элемент управления, в котором, в свою очередь, применяются функции, содержащиеся в полной версии платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Если приложение перенацелено на подмножество [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] и установлено в системе, где нет платформы [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)], то при попытке обратиться к функциям, отсутствующим в подмножестве [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], это приложение может работать неправильно.  
  
 Данное сообщение об "ошибке" фактически является только предупреждением; приложение по\-прежнему будет компилироваться.  Однако, возможен сбой позже в случае обращения элемента управления или библиотеки DLL к функциям, расположенным в отсутствующей сборке.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] — это подмножество полной библиотеки времени выполнения платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5.  Дополнительные сведения о веб\-службе [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] см. в разделе [Профиль клиента .NET Framework](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Чтобы исправить эту ошибку  
  
-   Удалите из проекта ссылку на указанную сборку или выполните нацеливание на полную версию платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] вместо библиотеки подмножества [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Дополнительные сведения о нацеливании на полную версию платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] см. в разделе [Практическое руководство. Определение целевой версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## См. также  
 [Целевая рабочая среда и целевая платформа](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Элемент Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Дополнительные ресурсы](../msbuild/additional-msbuild-resources.md)