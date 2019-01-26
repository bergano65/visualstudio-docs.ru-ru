---
title: Реализация обработки команд для вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 002ebd71eac8d9a39abc0a313d18a8efdcdc13cd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989186"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Реализация обработки команд для вложенных проектов
Интегрированной среде разработки можно передать команд, которые передаются через <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейсов вложенных проектов или родительские проекты можно отфильтровать или переопределить команды.  
  
> [!NOTE]
>  Можно отфильтровать только те команды, которые обычно обрабатываются в родительский проект. Команды, такие как **построения** и **развернуть** , обрабатываются интегрированной среды разработки не могут быть отфильтрованы.  
  
 Следующие шаги описывают процесс для реализации обработки команды.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-implement-command-handling"></a>Чтобы реализовать обработку команды  
  
1. Когда пользователь выбирает вложенного проекта или узла во вложенном проекте:  
  
   1. Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.  
  
      Или...  
  
   2. Если команда была создана в окне иерархии, например команды контекстного меню в обозревателе решений, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод родительского проекта.  
  
2. Родительский проект можно проверить параметры, передаваемые `QueryStatus`, такие как `pguidCmdGroup` и `prgCmds`, чтобы определить, должен ли родительский проект фильтра команды. Если родительский проект реализуется для фильтрации команд, она должна задать:  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    Затем родительский проект должен возвращать `S_OK`.  
  
    Если родительский проект не фильтрацию в команде, он должен просто вернуть `S_OK`. В этом случае интегрированной среды разработки автоматически направляет команду к дочернему проекту.  
  
    Для маршрутизации команды к дочернему проекту не имеет родительского проекта. Интегрированная среда разработки выполняет эту задачу...  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)