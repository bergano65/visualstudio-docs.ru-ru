---
title: Предоставление доступа к событиям в Visual Studio SDK | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02ddcf0c2321f6f4c07170117c6474b993c340f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Предоставление доступа к событиям в Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позволяет источником событий с помощью автоматизации. Корпорация Майкрософт рекомендует, чтобы вы источник события для проектов и элементов проектов.  
  
 События получаются путем автоматизации потребителей из <xref:EnvDTE.DTEClass.Events%2A> объекта или <xref:EnvDTE.DTEClass.GetObject%2A> («EventObjectName»). Среда вызывает метод `IDispatch::Invoke` с помощью `DISPATCH_METHOD` или `DISPATCH_PROPERTYGET` флаги для возврата при возникновении события.  
  
 Процесс объясняется, как возвращаются VSPackage связанные события.  
  
1.  Запускает среду.  
  
2.  Считывает из реестра все имена значений в группе автоматизации, AutomationEvents и AutomationProperties ключи всех пакетов VSPackage и сохраняет эти имена в таблице.  
  
3.  Вызывает объект-получатель автоматизации, в этом примере `DTE.Events.AutomationProjectsEvents` или `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  Среда находит параметр строки в таблице и загружает соответствующий пакет VSPackage.  
  
5.  Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод с помощью имени, переданный в вызов; в этом примере AutomationProjectsEvents или AutomationProjectItemsEvents.  
  
6.  VSPackage создается корневой объект, который содержит методы, такие как `get_AutomationProjectsEvents` и `get_AutomationProjectItemEvents` и затем возвращает указатель интерфейса IDispatch объекта.  
  
7.  Окружение вызывает соответствующий метод на основе имени, переданного в вызов автоматизации.  
  
8.  `get_` Метод создает другой объект события, основанный на IDispatch, который реализует интерфейс `IConnectionPointContainer` интерфейс и `IConnectionPoint` интерфейса и возвращает IDispatchpointer объекту.  
  
 Чтобы предоставить событие с помощью автоматизации, должен отвечать на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> и контрольных значений для строк, которые можно добавить в реестр. В этом примере базовый проект строки являются «BscProjectsEvents» и «BscProjectItemsEvents».  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Записи реестра из примера базового проекта  
 В этом разделе показано, куда нужно добавить в реестр значения событий автоматизации.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 «AutomationProjectEvents «=» возвращает объект AutomationProjectEvents»  
  
 «AutomationProjectItemEvents «=» возвращает объект AutomationProjectItemsEvents»  
  
|name|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|По умолчанию (@)|REG_SZ|Неиспользуемые|Не используется. Поля данных можно использовать для документации.|  
|AutomationProjectsEvents|REG_SZ|Имя объекта события.|Действителен только имя ключа. Поля данных можно использовать для документации.<br /><br /> В этом примере состоит из базового проекта образца.|  
|AutomationProjectItemEvents|REG_SZ|Имя объекта события|Действителен только имя ключа. Поля данных можно использовать для документации.<br /><br /> В этом примере состоит из базового проекта образца.|  
  
 При любых объектов событий запрашиваемые потребителя автоматизации, создайте корневой объект, который содержит методы для любых событий, поддерживающий VSPackage. Среда вызывает соответствующий `get_` метода для этого объекта. Например если `DTE.Events.AutomationProjectsEvents` вызове `get_AutomationProjectsEvents` вызова метода для корневого объекта.  
  
 ![События проекта Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Модель автоматизации для событий  
  
 Класс `CProjectEventsContainer` представляет исходный объект для BscProjectsEvents, пока `CProjectItemsEventsContainer` представляет исходный объект для BscProjectItemsEvents.  
  
 В большинстве случаев должен возвращать новый объект для каждого события запроса, так как большинство объектов событий принимают объект фильтра. Когда вызывается событие, проверьте этот фильтр, чтобы убедиться, что обработчик событий вызывается.  
  
 AutomationEvents.h и AutomationEvents.cpp содержат объявления и реализации классов в следующей таблице.  
  
|Класс|Описание|  
|-----------|-----------------|  
|`CAutomationEvents`|Реализует объект корневой события, полученные из `DTE.Events` объекта.|  
|`CProjectsEventsContainer` и `CProjectItemsEventsContainer`.|Реализуйте объекты источников событий, которые вызывают срабатывание соответствующих событий.|  
  
 В следующем примере кода показано, как для ответа на запрос для объекта события.  
  
```cpp  
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
  
 В представленном выше коде `g_wszAutomationProjects` имя коллекции проектов («FigProjects»), `g_wszAutomationProjectsEvents` («FigProjectsEvents») и `g_wszAutomationProjectItemsEvents` («FigProjectItemEvents») — это имена событий проекта и элементов проекта события, которые получают данные из вашей Реализация VSPackage.  
  
 Объекты событий получаются из одного центрального расположения, `DTE.Events` объекта. Таким образом, все объекты событий группируются вместе, чтобы конечный пользователь не имеет для просмотра всей объектной модели для поиска конкретного события. Это также позволяет предоставлять определенных объектах VSPackage, вместо необходимости реализовать собственный код для событий во всей системе. Однако для конечного пользователя, который необходимо найти событие для вашего `ProjectItem` интерфейса, это не очевидно, из которой извлекается этот объект события.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Примеры VSSDK](http://aka.ms/vs2015sdksamples)