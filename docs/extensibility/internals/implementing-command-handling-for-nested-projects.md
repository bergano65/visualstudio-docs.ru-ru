---
title: "Реализация команды для обработки вложенных проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71da10ee4473f3fb542e0ce0e03891d60b75d34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>Реализация команды обработки вложенных проектов
Интегрированной среде разработки можно передать команды, которые передаются через <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейсы для вложенных проектов или родительские проекты можно отфильтровать или переопределить команды.  
  
> [!NOTE]
>  Можно фильтровать только те команды, которые обычно обрабатываются родительский проект. Команды, такие как **построения** и **развернуть** , обрабатываются интегрированной среды разработки, не могут быть отфильтрованы.  
  
 Следующие шаги описывают процесс для реализации обработки команды.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-implement-command-handling"></a>Чтобы реализовать обработку команды  
  
1.  Когда пользователь выбирает вложенного проекта или узла в вложенного проекта:  
  
    1.  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.  
  
     Или...  
  
    1.  Если команда была создана в окне иерархии, например команды контекстного меню в обозревателе решений, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод родительского элемента проекта.  
  
2.  Родительский проект можно проверить параметры должны быть переданы `QueryStatus`, такие как `pguidCmdGroup` и `prgCmds`, чтобы определить, нужно ли применять фильтрацию команды родительский проект. Если родительский проект реализована для фильтрации команд, следует установить:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Родительский проект должна возвращать `S_OK`.  
  
     Если родительский проект не выполняет фильтрацию команды, она просто возвращает `S_OK`. В этом случае IDE автоматически направляет команду к дочернему проекту.  
  
     Родительский проект не имеет для маршрутизации к дочернему проекту команды. Интегрированная среда разработки выполняет эту задачу...  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)