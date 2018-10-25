---
title: Предоставление доступа к событиям в Visual Studio SDK | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96cbc9ad5c7098ff1aba2bc9cd3f387ca229cc98
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919893"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Предоставление доступа к событиям в пакете SDK для Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] позволяет источника события с помощью автоматизации. Рекомендуется, вы источник события для проектов и элементов проектов.  
  
 События получаются путем автоматизации потребителей от <xref:EnvDTE.DTEClass.Events%2A> объекта или <xref:EnvDTE.DTEClass.GetObject%2A> («EventObjectName»). Среда вызывает метод `IDispatch::Invoke` с помощью `DISPATCH_METHOD` или `DISPATCH_PROPERTYGET` флаги для возврата событие.  
  
 Следующий процесс объясняется, как возвращаются события определенного VSPackage.  
  
1. Среда начинает.  
  
2. Он считывает из реестра все имена значений в группе автоматизации, AutomationEvents и AutomationProperties ключи всех пакетов VSPackage и сохраняет эти имена в таблице.  
  
3. Потребитель автоматизации вызывает в этом примере `DTE.Events.AutomationProjectsEvents` или `DTE.Events.AutomationProjectItemsEvents`.  
  
4. Среда находит параметр строки в таблице и загружает соответствующий пакет VSPackage.  
  
5. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод с помощью имени, переданный в вызов; в этом примере AutomationProjectsEvents или AutomationProjectItemsEvents.  
  
6. VSPackage создается корневой объект, содержащий методы, такие как `get_AutomationProjectsEvents` и `get_AutomationProjectItemEvents` и возвращает указатель IDispatch объекта.  
  
7. Среда вызывает соответствующий метод на основе имени, переданного в вызов службы автоматизации.  
  
8. `get_` Метод создает другой объект событий на основе IDispatch, который реализует интерфейс `IConnectionPointContainer` интерфейс и `IConnectionPoint` интерфейс и возвращает IDispatchpointer на объект.  
  
   Чтобы предоставить событие с помощью автоматизации, вы должны ответить <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> и Контрольное значение для строки, добавляемые к реестру. В этом примере базовый проект строки являются «BscProjectsEvents» и «BscProjectItemsEvents».  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Записи реестра из примера базовый проект  
 В этом разделе показано, где для добавления значений событий автоматизации в реестр.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 «AutomationProjectEvents «=» возвращает объект AutomationProjectEvents»  
  
 «AutomationProjectItemEvents «=» возвращает объект AutomationProjectItemsEvents»  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|По умолчанию (@)|REG_SZ|неиспользуемые|Не используется. Поля данных можно использовать для документации.|  
|AutomationProjectsEvents|REG_SZ|Имя объекта события.|Относится только имя ключа. Поля данных можно использовать для документации.<br /><br /> Этот пример взят из образца базовый проект.|  
|AutomationProjectItemEvents|REG_SZ|Имя объекта события|Относится только имя ключа. Поля данных можно использовать для документации.<br /><br /> Этот пример взят из образца базовый проект.|  
  
 Если любой из ваших объектов событий запрашиваются потребителем автоматизации, создайте корневой объект, содержащий методы для любого события, которое поддерживает VSPackage. Среда вызывает соответствующий `get_` метод для этого объекта. Например если `DTE.Events.AutomationProjectsEvents` вызове `get_AutomationProjectsEvents` вызова метода на корневой объект.  
  
 ![События проекта Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Модель автоматизации для событий  
  
 Класс `CProjectEventsContainer` представляет исходный объект для BscProjectsEvents, хотя `CProjectItemsEventsContainer` представляет исходный объект для BscProjectItemsEvents.  
  
 В большинстве случаев должен возвращать новый объект для каждого запроса событий, так как большинство событий принимают объект фильтра. Когда событие, проверьте этот фильтр, чтобы убедиться, что обработчик событий вызывается.  
  
 AutomationEvents.h и AutomationEvents.cpp содержат объявления и реализации классов в следующей таблице.  
  
|Класс|Описание|  
|-----------|-----------------|  
|`CAutomationEvents`|Реализует объект корневого события, полученные из `DTE.Events` объекта.|  
|`CProjectsEventsContainer` и `CProjectItemsEventsContainer`|Реализации объектов источника событий, которые инициируют соответствующие события.|  
  
 В следующем примере кода показано, как ответить на запрос для объекта события.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 В приведенном выше коде в `g_wszAutomationProjects` имя коллекции проектов («FigProjects»), `g_wszAutomationProjectsEvents` («FigProjectsEvents») и `g_wszAutomationProjectItemsEvents` («FigProjectItemEvents») — это имена событий проекта и события, которые получают данные из элементов проекта вашей Реализация VSPackage.  
  
 Объекты событий извлекаются из одного центрального расположения, `DTE.Events` объекта. Таким образом, все объекты событий группируются вместе, чтобы конечный пользователь не имеет для просмотра всей объектной модели для поиска определенного события. Это также позволяет обеспечить определенных объектах VSPackage, вместо необходимости реализовать собственный код для системных событий. Тем не менее, для конечного пользователя, который необходимо найти событие для вашей `ProjectItem` интерфейса, это не очевидно, из которых извлекаются этот объект события.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Примеры VSSDK](../../misc/vssdk-samples.md)

