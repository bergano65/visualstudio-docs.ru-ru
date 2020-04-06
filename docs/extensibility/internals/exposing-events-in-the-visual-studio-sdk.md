---
title: Разоблачение событий в визуальной студии SDK (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708490"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Разоблачить события в Визуальной студии SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]позволяет исходить события с помощью автоматизации. Мы рекомендуем вам источник событий для проектов и элементов проекта.

 События извлекаются потребителями <xref:EnvDTE.DTEClass.Events%2A> автоматизации <xref:EnvDTE.DTEClass.GetObject%2A> с объекта `GetObject("EventObjectName")`или (например, ). Среда вызывает `IDispatch::Invoke` с `DISPATCH_METHOD` помощью флагов или `DISPATCH_PROPERTYGET` флагов для возврата события.

 Следующий процесс объясняет, как возвращаются события, связанные с VSPackage.

1. Начинается среда.

2. Он читает из реестра все имена значений под **автоматизации,** **AutomationEvents**, и **AutomationProperties** ключи всех VSPackages, и хранит эти имена в таблице.

3. В этом примере `DTE.Events.AutomationProjectsEvents` потребитель `DTE.Events.AutomationProjectItemsEvents`автоматизации вызывает вызовы или .

4. Среда находит параметр строки в таблице и загружает соответствующий VSPackage.

5. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, используя имя, передаваемое в вызове; в этом `AutomationProjectsEvents` примере, или `AutomationProjectItemsEvents`.

6. VSPackage создает корневой объект, который `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` имеет такие методы, как, а затем возвращает указатель IDispatch объекту.

7. Среда вызывает соответствующий метод на основе имени, передаваемого в вызов автоматизации.

8. Метод `get_` создает другой объект событий на основе IDispatch, который реализует `IConnectionPointContainer` интерфейс и `IConnectionPoint` интерфейс и возвращает `IDispatchpointer` объект.

   Чтобы разоблачить событие с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> автоматизации, вы должны реагировать и следить за строки, которые вы добавляете в реестр. В примере Базового проекта строки *BscProjectsEvents* и *BscProjectItems.*

## <a name="registry-entries-from-the-basic-project-sample"></a>Записи реестра из образца базового проекта
 В этом разделе показано, где добавлять значения событий автоматизации в реестр.

 **«HKEY_LOCAL_MACHINE»-ПРОГРАММНО-ИСПАНЦИЯ»-Визуальнаястудия»8.0 »Пакеты\\<PkgGUID\>«АвтоматизацияСобытия»**

 **AutomationProjectEvents** - `AutomationProjectEvents` возвращает объект.

 **AutomationProjectItemEvents** - `AutomationProjectItemsEvents` возвращает объект.

|name|Type|Диапазон|Описание|
|----------|----------|-----------|-----------------|
|По умолчанию (кв. м)|REG_SZ|Не используется|Не используется. Можно использовать поле данных для документации.|
|*АвтоматизацияПроектыСобытия*|REG_SZ|Имя объекта события.|Только ключевое имя имеет отношение. Можно использовать поле данных для документации.<br /><br /> Этот пример взят из примера Базового проекта.|
|*АвтоматизацияПроектТемСобытия*|REG_SZ|Имя объекта события|Только ключевое имя имеет отношение. Можно использовать поле данных для документации.<br /><br /> Этот пример взят из примера Базового проекта.|

 Когда любой из объектов вашего события запрашивается потребителем автоматизации, создайте корневой объект с методами для любого события, поддерживаемого вашим VSPackage. Среда вызывает соответствующий `get_` метод на этом объекте. Например, `DTE.Events.AutomationProjectsEvents` если называется, вызывается `get_AutomationProjectsEvents` метод на корневом объекте.

 ![Мероприятия проекта Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents") Модель автоматизации событий

 Класс `CProjectEventsContainer` представляет исходный объект для *BscProjectsEvents*и `CProjectItemsEventsContainer` представляет исходный объект для *BscProjectItems.*

 В большинстве случаев необходимо вернуть новый объект для каждого запроса события, поскольку большинство объектов событий занимают объект фильтра. При запуске события проверьте этот фильтр, чтобы убедиться, что обработчик событий вызывается.

 *AutomationEvents.h* и *AutomationEvents.cpp* содержат декларации и реализации классов в следующей таблице.

|Class|Описание|
|-----------|-----------------|
|`CAutomationEvents`|Реализует корневой объект события, `DTE.Events` извлеченный из объекта.|
|`CProjectsEventsContainer` и `CProjectItemsEventsContainer`|Реализация объектов источника события, которые заражали соответствующие события.|

 Следующий пример кода показывает, как ответить на запрос объекта события.

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

 В приведенном `g_wszAutomationProjects` выше коде приведено название вашей `g_wszAutomationProjectsEvents` коллекции проектов `g_wszAutomationProjectItemsEvents` *(FigProjects),*(*FigProjectsEvents)* и *(FigProjectItemEvents)*— это имена событий проекта и событий элементов проекта, которые получены из реализации VSPackage.

 Объекты событий извлекаются из того `DTE.Events` же центрального местоположения объекта. Таким образом, все объекты событий сгруппированы так, что конечный пользователь не должен просматривать всю модель объекта, чтобы найти конкретное событие. Это также позволяет предоставлять конкретные объекты VSPackage, вместо того, чтобы требовать от вас реализовать свой собственный код для общесистемных событий. Однако для конечном пользователя, который должен `ProjectItem` найти событие для вашего интерфейса, не сразу ясно, откуда извлекается объект события.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
