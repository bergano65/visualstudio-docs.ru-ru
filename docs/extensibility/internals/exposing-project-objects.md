---
title: "Предоставление доступа к объектам проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "объекты проекта, предоставление"
  - "расширяемость, объекты проекта"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Предоставление доступа к объектам проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пользовательский проект типы могут предоставлять объекты автоматизации, чтобы разрешить доступ к проекту, с помощью интерфейсов автоматизации. Каждый тип проекта должен предоставлять стандартные <xref:EnvDTE.Project> объект автоматизации, доступном из <xref:EnvDTE.Solution>, содержит коллекцию всех проектов, которые открыты в Интегрированной среде разработки. Каждый элемент в проекте должен предоставляться <xref:EnvDTE.ProjectItem> объект, к которому с <xref:Project.ProjectItems>. Помимо этих объектов автоматизации стандартных проектов можно выбрать объекты автоматизации проектов предложения.  
  
 Можно создать пользовательскую автоматизацию корневого уровня объекта, которые можно получить доступ к позднего связывания из объекта DTE root с помощью `DTE.<customeObjectName>` или `DTE.GetObject(“<customObjectName>”)`. Например Visual C\+\+ создает коллекцию проектов, зависящих от проекта C\+\+ с именем «"vcprojects"», можно получить доступ с помощью DTE. "Vcprojects" или DTE. GetObject\("VCProjects"\). Можно также создать Project.Object, который является уникальным для проекта тип Project.CodeModel, который можно запрашивать его самого производного объекта, ProjectItem, который предоставляет ProjectItem.Object и ProjectItem.FileCodeModel.  
  
 Распространенной практикой для проектов для предоставления коллекции пользовательских, относящихся к проекту проекта является. Например [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] создает коллекцию конкретного проекта C\+\+, затем можно получить доступ с помощью `DTE.VCProjects` или `DTE.GetObject("VCProjects")`. Можно также создать `Project.Object`, который является уникальным для типа проекта, `Project.CodeModel`, которой можно запрашивать его самого производного объекта `ProjectItem`, который предоставляет `ProjectItem.Object`, и `ProjectItem.FileCodeModel`.  
  
### Принять участие объект VSPackage для проекта  
  
1.  Добавьте соответствующие ключи из VSPackage pkgdef\-файл.  
  
     Например вот .pkgdef параметры проекта на языке C\+\+.  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Реализация кода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метода, как показано в следующем примере.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     В коде `g_wszAutomationProjects` имя коллекции проектов.`GetAutomationProjects` Метод создает объект, реализующий интерфейс `Projects` интерфейс и возвращает `IDispatch` указатель на вызывающий объект, как показано в следующем примере кода.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     Необходимо выбрать уникальное имя для объекта автоматизации. Конфликты имен непредсказуемы и вызывают конфликты с конфликтующим именем объекта, сколь угодно исключение если несколько типов проектов использовать то же имя. Должен включать название организации или некоторых уникальных аспектов его имя продукта, имя объекта автоматизации.  
  
     Пользовательская `Projects` объект коллекции — это точка входа для удобства для оставшейся части проекта модели автоматизации. Объект проекта, также доступен из <xref:EnvDTE.Solution> коллекции проектов. После создания соответствующего кода и записей реестра, предоставляющие потребителям с `Projects` коллекцию объектов, реализации необходимо указать оставшиеся стандартные объекты модели проекта. Для получения дополнительной информации см. [Проект моделирования](../../extensibility/internals/project-modeling.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>