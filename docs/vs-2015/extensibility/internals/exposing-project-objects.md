---
title: Предоставление доступа к объектам проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c949d4668089a2cc06543169a1c3ce6619409d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990708"
---
# <a name="exposing-project-objects"></a>Предоставление доступа к объектам проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользовательские типы проектов, чтобы разрешить доступ к проекту с помощью интерфейсов автоматизации, можно предоставить объекты автоматизации. Любой тип проекта должен предоставлять стандартные <xref:EnvDTE.Project> объект автоматизации, к которому осуществляется из <xref:EnvDTE.Solution>, которое содержит коллекцию всех проектов, которые открыты в интегрированной среде разработки. Каждый элемент в проекте должен предоставляться <xref:EnvDTE.ProjectItem> доступ к которому осуществляется с помощью <xref:EnvDTE.Project.ProjectItems>. Помимо этих объектов автоматизации standard проектов может выбрать предоставление объектов автоматизации проектов.  
  
 Можно создать пользовательские корневого уровня объектов автоматизации, к которым можно обращаться с поздним связыванием из объекта DTE корневого, используя `DTE.<customeObjectName>` или `DTE.GetObject(“<customObjectName>”)`. Например Visual C++ создает коллекцию проектов конкретного проекта C++ с именем «"vcprojects"», доступны с помощью DTE. "Vcprojects" или DTE. GetObject("VCProjects"). Можно также создать Project.Object, который является уникальным для типа проекта, Project.CodeModel, который можно запрашивать его самого производного объекта, объект ProjectItem, который предоставляет ProjectItem.Object и ProjectItem.FileCodeModel.  
  
 Это распространенный способ для проектов для предоставления коллекции проектов пользовательских, относящихся к проекту. Например [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] создает коллекцию конкретного проекта C++, которая затем доступны с помощью `DTE.VCProjects` или `DTE.GetObject("VCProjects")`. Вы также можете создать `Project.Object`, который является уникальным для типа проекта, `Project.CodeModel`, который можно запросить для его самого производного объекта `ProjectItem`, предоставляющий `ProjectItem.Object`и `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Для передачи объекта определенного VSPackage для проекта  
  
1.  Добавьте соответствующие ключи для вашего VSPackage pkgdef-файл.  
  
     Например ниже приведены параметры .pkgdef для проекта на языке C++.  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Реализация кода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, как показано в следующем примере.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     В коде `g_wszAutomationProjects` имя коллекции проектов. `GetAutomationProjects` Метод создает объект, реализующий `Projects` и возвращающий `IDispatch` указатель на вызывающий объект, как показано в следующем примере кода.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Вы должны выбрать уникальное имя для объекта автоматизации. Конфликты имен непредсказуемы, в результате чего конфликтов конфликтующим именем объекта произвольно исключение если несколько типов проектов используйте то же имя. Следует включить название организации или некоторых уникальных аспектов его название продукта, имя объекта автоматизации.  
  
     Пользовательский `Projects` объект коллекции — это точка входа удобства для оставшейся части проекта модели автоматизации. Объект проекта, также доступен из <xref:EnvDTE.Solution> коллекции проектов. После создания в соответствующих записях код и реестра, которые предоставляют заказчикам `Projects` коллекция объектов, реализации необходимо указать оставшиеся стандартные объекты для модели проекта. Дополнительные сведения см. в разделе [проекта моделирования](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
