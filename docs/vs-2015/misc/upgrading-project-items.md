---
title: Обновление элементов проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698687"
---
# <a name="upgrading-project-items"></a>Обновление элементов проекта
При добавлении элементов или управлении ими в системах проектов, которые не реализуются, может потребоваться участие в процессе обновления проекта. Crystal Reports — это пример элемента, который можно добавить в систему проектов.  
  
 Как правило, разработчики элементов проекта хотят использовать уже полностью созданный и обновленный проект, так как им нужно знать, что такое ссылки на проект и какие другие свойства проекта должны принять решение об обновлении.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Получение уведомления об обновлении проекта  
  
1. Установите <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> флаг (определенный в vsshell80. IDL) в реализации элемента проекта. Это приведет к автоматической загрузке пакета VSPackage элемента проекта, когда [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] оболочка определит, что система проектов находится в процессе обновления.  
  
2. Порекомендуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> метод.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Интерфейс срабатывает после того, как реализация системы проекта завершит свои операции обновления и будет создан новый обновленный проект. В зависимости от сценария <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> интерфейс срабатывает после <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> методов, или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>Обновление файлов элементов проекта  
  
1. Необходимо тщательно управлять процессом резервного копирования файлов в реализации элемента проекта. Это относится к параллельной резервной копии, где `fUpgradeFlag` параметр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метода имеет значение <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , где файлы, для которых была создана резервная копия, помещаются в файлы параллельных файлов, обозначенные как "Old". Резервные копии файлов старше системного времени, когда проект был обновлен, можно назначить как устаревшие. Кроме того, они могут быть перезаписаны, если не предпринять конкретные меры по предотвращению этого.  
  
2. Когда элемент проекта получает уведомление об обновлении проекта, **Мастер преобразования Visual Studio** по-прежнему отображается. Поэтому следует использовать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> интерфейса для предоставления сообщений об обновлении пользовательскому интерфейсу мастера.  
  
## <a name="see-also"></a>См. также:  
 [Мастер преобразования Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Обновление пользовательских проектов](../misc/upgrading-custom-projects.md)