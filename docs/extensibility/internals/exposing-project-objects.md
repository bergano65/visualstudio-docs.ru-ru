---
title: "Предоставление доступа к объектам проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f29ca84669f563da5733c8c07b219d498ccf6ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-project-objects"></a>Предоставление доступа к объектам в проекте
Пользовательский проект типы могут предоставлять объекты автоматизации, чтобы разрешить доступ к проекту с помощью интерфейсов автоматизации. Каждый тип проекта должен предоставлять стандартные <xref:EnvDTE.Project> объект автоматизации, к которому осуществляется из <xref:EnvDTE.Solution>, которое содержит коллекцию всех проектов, которые открыты в Интегрированной среде разработки. Каждый элемент в проекте должен предоставляться <xref:EnvDTE.ProjectItem> объект, к которому с `Project.ProjectItems`. Помимо этих объектов автоматизации standard проектов можно выбрать объекты автоматизации проектов предложения.  
  
 Можно создать специализированная автоматизация корневого уровня объекта, которые можно получить доступ к поздним связыванием из объекта DTE основных с помощью `DTE.<customeObjectName>` или `DTE.GetObject("<customObjectName>")`. Например Visual C++ создает коллекцию проектов для конкретного проекта C++ с именем «"vcprojects"», можно получить доступ с помощью DTE. "Vcprojects" или DTE. GetObject("VCProjects"). Можно также создать Project.Object, который является уникальным для типа проекта Project.CodeModel, которые можно запросить для его объекта более низкого уровня, элемента проекта, который предоставляет ProjectItem.Object и ProjectItem.FileCodeModel.  
  
 Распространенной практикой для проектов, чтобы предоставить коллекцию проектов пользовательских, относящихся к проекту является. Например [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] создает коллекцию определенных проектов C++, можно затем использовать, с помощью `DTE.VCProjects` или `DTE.GetObject("VCProjects")`. Можно также создать `Project.Object`, который является уникальным для типа проекта, `Project.CodeModel`, которой можно запрашивать его самого производного объекта `ProjectItem`, который предоставляет `ProjectItem.Object`и `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Добавлять объект VSPackage для проекта  
  
1.  Добавьте соответствующие ключи для вашего VSPackage pkgdef-файл.  
  
     Например ниже приведены параметры .pkgdef для проекта на языке C++.  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Реализация кода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метода, как показано в следующем примере.  
  
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
  
     В коде `g_wszAutomationProjects` имя коллекции проектов. `GetAutomationProjects` Метод создает объект, реализующий интерфейс `Projects` интерфейс и возвращает `IDispatch` указателя в вызывающий объект, как показано в следующем примере кода.  
  
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
  
     Необходимо выбрать уникальное имя для объекта автоматизации. Конфликты имен непредсказуемы, и конфликты вызвать с конфликтующим именем объекта произвольно исключение если в нескольких типах проектов использовать то же имя. Следует включить название организации или некоторые уникальные аспектом его название продукта, имя объекта автоматизации.  
  
     Пользовательский `Projects` объект коллекции — это точка входа удобства для оставшейся части проекта модели автоматизации. Объект проекта, который можно вызвать с <xref:EnvDTE.Solution> коллекции проектов. После создания соответствующий код и записей реестра, предоставляющие потребителям с `Projects` коллекция объектов, такой реализации необходимо указать оставшиеся стандартные объекты для модели проекта. Дополнительные сведения см. в разделе [проекта моделирования](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>