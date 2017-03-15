---
title: "Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "обновление приложений, Visual Studio"
  - "обновление проектов [Visual Studio]"
  - "проекты [Visual Studio], обновление"
  - "мастер преобразования Visual Studio"
  - "мастер преобразования"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Иногда Visual Studio не удается полностью преобразовать проект, созданный в более ранней версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Если советы в следующих разделах не позволят вам решить свою проблему, возможно, вы найдете дополнительные сведения на [Вики\-сайте TechNet: портал разработки](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## Проект не запускается, поскольку не удалось найти файлы  
 Файл проекта содержит жестко заданные пути к файлам, которые используются в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска проекта при нажатии клавиши F5.  В числе этих путей может быть расположение файла devenv.exe и других обязательных файлов.  В обновленной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пути к этим файлам могут быть изменены.  
  
#### Исправление неправильных путей  
  
1.  Откройте файл проекта в текстовом редакторе.  
  
2.  Внимательно проверьте наличие неправильных путей к файлам, особенно тех, которые содержат номер версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Измените неправильные пути к файлам, чтобы они указывали на новые конечные объекты.  
  
## Построение проекта не запускается, поскольку ссылки недопустимы  
 При обновлении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], возможно, также выполняется обновление версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Если проект содержит ссылки, не используемые в более новой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], они могут не разрешаться правильно.  Это особенно вероятно для ссылок, включающих номера версий, например `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Если код содержит много недопустимых ссылок, простейшим решением может стать применение функции настройки для различных сред [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с целью настройки на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Разрешение неверных ссылок  
  
1.  Откройте файл проекта в текстовом редакторе.  
  
2.  Откройте свойства проекта.  
  
3.  Выделите верное значение для параметра **Целевая рабочая среда**.  Также можно изменить значение элемента `<TargetFrameworkVersion>` непосредственно в файле проекта.  
  
 Если вы хотите, чтобы проект выполнялся в обновленной версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], необходимо обновить ссылки проекта, а также любые операторы `Imports` или `Using`, вызывающие эти ссылки.  Если проект загружается в интегрированной среде разработки, можно обновить ссылки с помощью **Обозревателя решений** или **Диспетчера ссылок**.  
  
## См. также  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)