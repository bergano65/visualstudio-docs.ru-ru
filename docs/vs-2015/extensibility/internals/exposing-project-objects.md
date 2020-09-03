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
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196643"
---
# <a name="exposing-project-objects"></a>Предоставление доступа к объектам проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользовательские типы проектов могут предоставлять объекты автоматизации, чтобы обеспечить доступ к проекту с помощью интерфейсов автоматизации. Предполагается, что каждый тип проекта предоставляет стандартный <xref:EnvDTE.Project> объект автоматизации, к которому осуществляется доступ из <xref:EnvDTE.Solution> , который содержит коллекцию всех проектов, открытых в интегрированной среде разработки. Предполагается, что каждый элемент в проекте предоставляется <xref:EnvDTE.ProjectItem> объектом, к которому обращается <xref:EnvDTE.Project.ProjectItems> . В дополнение к этим стандартным объектам автоматизации, проекты могут предлагать специальные объекты автоматизации проекта.  
  
 Можно создать пользовательские объекты автоматизации на корневом уровне, к которым можно получить доступ с поздним связыванием из корневого объекта DTE с помощью `DTE.<customeObjectName>` или `DTE.GetObject(“<customObjectName>”)` . Например, Visual C++ создает коллекцию проектов C++ для конкретного проекта с именем «Вкпрожектс», доступ к которой можно получить с помощью DTE. Вкпрожектс или DTE. GetObject ("Вкпрожектс"). Можно также создать проект. Object, уникальный для типа проекта, проект. CodeModel, который можно запрашивать для наиболее производного объекта, объект ProjectItem, предоставляющий объект ProjectItem. Object и объект ProjectItem. Филекодемодел.  
  
 Это распространенное соглашение для проектов с целью предоставления настраиваемой коллекции проектов для конкретного проекта. Например, [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] создает коллекцию проектов на C++, доступ к которой можно получить с помощью `DTE.VCProjects` или `DTE.GetObject("VCProjects")` . Можно также создать объект `Project.Object` , который является уникальным для типа проекта, `Project.CodeModel` который можно запрашивать для наиболее производного объекта, `ProjectItem` , который предоставляет `ProjectItem.Object` и `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Добавление в проект объекта, относящегося к VSPackage  
  
1. Добавьте соответствующие ключи в файл pkgdef пакета VSPackage.  
  
     Например, ниже приведены параметры. pkgdef для проекта языка C++.  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Реализуйте код в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> методе, как показано в следующем примере.  
  
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
  
     В коде `g_wszAutomationProjects` — это имя коллекции проектов. `GetAutomationProjects`Метод создает объект, реализующий интерфейс, `Projects` и возвращает `IDispatch` указатель на вызывающий объект, как показано в следующем примере кода.  
  
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
  
     Необходимо выбрать уникальное имя для объекта автоматизации. Конфликты имен непредсказуемы, а конфликты приводят к тому, что конфликтующее имя объекта будет произвольно выдаваться, если несколько типов проектов используют одно и то же имя. В имя объекта автоматизации следует включить название организации или уникальный аспект имени продукта.  
  
     Пользовательский `Projects` объект коллекции является удобной точкой входа для оставшейся части модели автоматизации проекта. Объект Project также доступен из <xref:EnvDTE.Solution> коллекции проектов. После создания соответствующего кода и записей реестра, предоставляющих потребителей `Projects` объектам коллекции, ваша реализация должна предоставлять оставшиеся стандартные объекты для модели проекта. Дополнительные сведения см. в разделе [Моделирование проектов](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
