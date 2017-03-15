---
title: "Обновление элементов проекта | Microsoft Docs"
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
  - "обновление элементов проекта"
  - "проекты [Visual Studio SDK], обновление элементов"
  - "элементы проекта [Visual Studio], обновление"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Обновление элементов проекта
При добавлении или управлять элементы в системах, то проекта не реализуется, можно участвовать в процессе обновления проекта.  Кристаллические отчеты пример элемента, который можно добавить к системе проектов.  
  
 Обычно реализации элемента проекта хотят использовать уже полностью создается и обновленного проекта, поскольку им требуется знать, что ссылки проекта и другие свойства проекта существует для принятия решения обновления.  
  
### Получить уведомление обновления проектов  
  
1.  Установка <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> пометить \(заданный в vsshell80.idl\) в реализации элемента проекта.  Это приводит к тому, что элемент проекта при автоматической загрузки VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочка указывает, что система проектов в процессе обновления.  
  
2.  Посоветуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> интерфейс посредством  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> метод.  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс после реализации системы проектов выполнить свои операции обновления и новый обновленный проект создан.  В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> интерфейс после  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>"  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> или  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>методы.  
  
### Обновление файлов элемента проекта  
  
1.  Необходимо тщательно управления процессом резервных копий файлов в реализации элемента проекта.  Это применяется в частности для параллельной резервной копии, где <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> параметр   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>метод имеет значение  `fUpgradeFlag`, где были сохранены файлы, которые расположены вдоль боковые файлов, которые обозначены как ".old".  Поддерживанные файлы старше системное время, когда проект был обновлен можно назначить в качестве несвежое.  Кроме того, они могут быть перезаписаны, если не предпринимать соответствующие меры для предотвращения этого.  
  
2.  Элемент проекта во время обновления проектов, принимающий уведомление **Мастер преобразования Visual Studio** все еще отображается.  Поэтому необходимо использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейс для реализации сообщения обновления пользовательский интерфейс мастера.  
  
## См. также  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/ru-ru/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md)