---
title: Разоблачение объектов проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708474"
---
# <a name="expose-project-objects"></a>Экспозиция объектов проекта

Пользовательские типы проектов могут обеспечить объекты автоматизации, чтобы обеспечить доступ к проекту с помощью интерфейсов автоматизации. Каждый тип проекта должен <xref:EnvDTE.Project> предоставить стандартный объект <xref:EnvDTE.Solution>автоматизации, который доступен из , который содержит коллекцию всех проектов, которые открыты в IDE. Каждый элемент проекта, как ожидается, будет выставлен объектом, <xref:EnvDTE.ProjectItem> доступ к нему с `Project.ProjectItems`. В дополнение к этим стандартным объектам автоматизации, проекты могут предложить конкретные объекты автоматизации проекта.

Можно создать пользовательские объекты автоматизации корневого уровня, которые можно `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")`получить доступ к поздним схватам с корневого объекта DTE с помощью или. Например, Visual C е создает специальную коллекцию проектов, называемую *VCProjects,* доступ к которым можно получить `DTE.VCProjects` или `DTE.GetObject("VCProjects")`. Вы также можете `Project.Object`создать, который является уникальным `Project.CodeModel`для типа проекта, который может быть запрошен для `ProjectItem`его наиболее производных объектов, и , который подвергает `ProjectItem.Object` и `ProjectItem.FileCodeModel`.

Это общая конвенция для проектов, чтобы разоблачить пользовательские, конкретные проекты коллекции. Например, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] создается специальная коллекция проектов, к `DTE.VCProjects` `DTE.GetObject("VCProjects")`которым можно получить доступ с помощью или . Вы также можете `Project.Object`создать, который является уникальным `Project.CodeModel`для типа проекта, который может быть запрошен `ProjectItem`для его `ProjectItem.Object`наиболее `ProjectItem.FileCodeModel`производных объектов, a , который подвергает , и .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Вносить объект для проекта для участия в проекте для конкретного vsPackage

1. Добавьте соответствующие ключи в файл *.pkgdef* вашего VSPackage.

     Например, вот настройки *.pkgdef* для проекта языка СЗ:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Реализация кода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> методе, как и в следующем примере.

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

     В коде `g_wszAutomationProjects` — название вашей коллекции проектов. Метод `GetAutomationProjects` создает объект, который `Projects` реализует интерфейс `IDispatch` и возвращает указатель объекту вызова, как показано в следующем примере кода.

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

     Выберите уникальное имя для объекта автоматизации. Конфликты имен непредсказуемы, и коллизии приводят к произвольному выброшению имени объекта, если несколько типов проектов используют одно и то же имя. Вы должны включить свое корпоративное имя или какой-либо уникальный аспект названия продукта в название объекта автоматизации.

     Объект `Projects` пользовательского сбора является удобной точкой входа для оставшейся части модели автоматизации проекта. Объект проекта также доступен <xref:EnvDTE.Solution> из коллекции проекта. После создания соответствующего кода и записей реестра, `Projects` которые предоставляют потребителям объекты сбора, ваша реализация должна предоставить оставшиеся стандартные объекты для модели проекта. Для получения дополнительной [информации](../../extensibility/internals/project-modeling.md)см.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
