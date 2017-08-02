---
title: "Предоставление событий в Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Предоставление событий [Visual Studio]"
  - "автоматизация [Visual Studio SDK], предоставление событий"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Предоставление событий в Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позволяет источником событий с помощью автоматизации. Корпорация Майкрософт рекомендует, чтобы вы источник события для проектов и элементов проектов.  
  
 Потребители автоматизации из получаются события <xref:EnvDTE.DTEClass.Events%2A> объекта или <xref:EnvDTE.DTEClass.GetObject%2A> («EventObjectName»). Среда вызывает `IDispatch::Invoke` с помощью `DISPATCH_METHOD` или `DISPATCH_PROPERTYGET` флаги для получения события.  
  
 Процесс объясняется, как возвращаются события VSPackage.  
  
1.  Запускает среду.  
  
2.  Считывает из реестра все имена значений в разделе Автоматизация, AutomationEvents и AutomationProperties ключи всех VSPackages и сохраняет эти имена в таблице.  
  
3.  Вызывает потребителя автоматизации, в этом примере `DTE.Events.AutomationProjectsEvents` или `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  Среда находит параметр строки в таблице и загружает соответствующий пакет VSPackage.  
  
5.  Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод с помощью имени передается в вызов, в этом примере, AutomationProjectsEvents или AutomationProjectItemsEvents.  
  
6.  VSPackage создает корневой объект, который содержит методы, такие как `get_AutomationProjectsEvents` и `get_AutomationProjectItemEvents` и возвращает указатель IDispatch объекта.  
  
7.  Среда вызывает соответствующий метод, основанный на имени, переданного в вызов автоматизации.  
  
8.   `get_` Метод создает другой объект событий на основе интерфейса IDispatch, который реализует интерфейс `IConnectionPointContainer` интерфейс и `IConnectionPoint` интерфейс и возвращает объект IDispatchpointer.  
  
 Чтобы предоставить событие с помощью автоматизации, вы должны ответить <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> и контрольных значений для строк, которые можно добавить в реестр. В этом примере базовый проект строки являются «BscProjectsEvents» и «BscProjectItemsEvents».  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Записи реестра из примера базового проекта  
 В этом разделе показано, куда нужно добавить в реестр значения событий автоматизации.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 «AutomationProjectEvents «=» возвращает объект AutomationProjectEvents»  
  
 «AutomationProjectItemEvents «=» возвращает объект AutomationProjectItemsEvents»  
  
|Имя|Тип|Диапазон|Описание|  
|----------|----------|-----------|-----------------|  
|По умолчанию (@)|REG_SZ|Неиспользуемые|Не используется. Поля данных можно использовать документацию.|  
|AutomationProjectsEvents|REG_SZ|Имя объекта события.|Действителен только имя ключа. Поля данных можно использовать документацию.<br /><br /> Этот пример взят из образца базового проекта.|  
|AutomationProjectItemEvents|REG_SZ|Имя объекта события|Действителен только имя ключа. Поля данных можно использовать документацию.<br /><br /> Этот пример взят из образца базового проекта.|  
  
 Когда потребитель автоматизации запрашиваемых всех объектов событий, создайте корневой объект, который содержит методы для любого события, которое поддерживает VSPackage. Среда вызывает соответствующий `get_` этого объекта. Например если `DTE.Events.AutomationProjectsEvents` вызове `get_AutomationProjectsEvents` был вызван метод на корневой объект.  
  
 ![События проекта Visual Studio](~/extensibility/internals/media/projectevents.gif "ProjectEvents")  
Модель автоматизации для события  
  
 Класс `CProjectEventsContainer` представляет исходный объект для BscProjectsEvents, а `CProjectItemsEventsContainer` представляет исходный объект для BscProjectItemsEvents.  
  
 В большинстве случаев должны возвращать новый объект для каждого запроса событий большинство объектов событий занять объект фильтра. При вызове события, проверьте этот фильтр, чтобы убедиться, что вызывается обработчик события.  
  
 AutomationEvents.h и AutomationEvents.cpp содержат объявления и реализации классов в следующей таблице.  
  
|Класс|Описание|  
|-----------|-----------------|  
|`CAutomationEvents`|Реализует объект корневого события, полученные из `DTE.Events` объекта.|  
|`CProjectsEventsContainer` и `CProjectItemsEventsContainer`.|Реализуйте объекты источников событий, которые инициируют соответствующие события.|  
  
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
  
 В приведенном выше коде `g_wszAutomationProjects` имя коллекции проектов («FigProjects»), `g_wszAutomationProjectsEvents` («FigProjectsEvents») и `g_wszAutomationProjectItemsEvents` («FigProjectItemEvents») — это имена событий проекта и элементов проекта события, которые получают данные из вашей реализации VSPackage.  
  
 Объекты событий получаются из центрального расположения, `DTE.Events` объект. Таким образом, все объекты событий группируются вместе, чтобы конечный пользователь не имеет для просмотра всей объектной моделью, чтобы найти конкретное событие. Это также позволяет предоставлять определенные объекты VSPackage, вместо необходимости реализовать собственный код для системных событий. Однако для конечного пользователя, который необходимо найти событие для вашего `ProjectItem` интерфейс, это не очевидно, из которой извлекается этот объект события.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Образцы VSSDK](../../misc/vssdk-samples.md)