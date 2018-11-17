---
title: Инициализация последовательности подтипов проекта | Документация Майкрософт
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
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53c0a474a5a5caf887599bc50e623bd25e7be782
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746521"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Инициализация последовательности подтипов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Среды создает проект путем вызова реализации базового проекта фабрики <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Конструирование подтипом проекта запускается, когда среда определяет, что список GUID типа проекта для расширения файл проекта не пуста. Расширение файла проекта и идентификатор GUID проекта укажите информацию о том, будет ли проект [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../../includes/csprcs-md.md)] тип проекта. Например, расширение .vbproj и определить {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] проекта.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Инициализация среды подтипов проекта  
 В следующей процедуре подробно последовательность инициализации для системы проектов, упорядоченные по несколько подтипов проекта.  
  
1. Среда вызывает базовый проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, и хотя проект анализирует его файл проекта обнаруживает, что тип агрегатного проекта список идентификаторов GUID не `null`. Проект прекращает непосредственном создании своего проекта.  
  
2. Вызовы проекта `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> службы для создания подтипом проекта, с помощью реализации среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метод. В этом методе среды делает рекурсивные вызовы функции для реализации методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> методов, хотя он проход по списку проекта введите идентификаторы GUID, начиная с подтип внешний проект.  
  
    Далее описаны действия по инициализации.  
  
   1.  Реализация среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> вызовы методов "HrCreateInnerProj'' ' метод со следующим объявлением функции:  
  
       ```  
       HRESULT HrCreateInnerProj  
       (  
           WCHAR *pwszGuids,  
           IUnknown *pOuter,  
           IVsAggregatableProject *pOwner,  
           LPCOLESTR pszFilename,  
           LPCOLESTR pszLocation,  
           LPCOLESTR pszName,  
           VSCREATEPROJFLAGS grfCreateFlags,  
           IUnknown **ppInner,  
           BOOL *pfCancelled  
       )  
       ```  
  
        Когда эта функция вызывается в первый раз, то есть для подтипа внешний проект, параметры `pOuter` и `pOwner` передаются в качестве `null` и функция задает подтип внешний проект `IUnknown` для `pOuter`.  
  
   2.  Далее среда вызывает `HrCreateInnerProj` функцию со второй GUID типа проекта в списке. Этот идентификатор GUID соответствует второй внутренний подтип проекта шаг с заходом направлении базового проекта в последовательности статистической обработки.  
  
   3.  `pOuter` Теперь указывают на `IUnknown` подтипа внешний проект, и `HrCreateInnerProj` вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> последующим вызовом реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> метод передается в управлении `IUnknown` подтипа внешний проект, `pOuter`. Принадлежащий проект (внутренний подтип проекта) должен создать свой объект агрегатного проекта. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> передается указатель на реализацию метода `IUnknown` внутреннего проекта, который агрегируется. Эти два метода создания объекта агрегата и реализации необходимо соблюдать правила модели COM статистической обработки, чтобы убедиться, что подтип проекта не в итоге содержит счетчик ссылок на себя.  
  
   4.  `HrCreateInnerProj` вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. В этом методе подтипа проекта выполняет свою работу инициализации. Можно например, зарегистрировать события решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
   5.  `HrCreateInnerProj` вызывается рекурсивно, пока не будет достигнут последний идентификатор GUID (базовый проект) в списке. Для каждого из этих вызовов шаги c-d, повторяются. `pOuter` Указывает подтип внешний проект `IUnknown` для каждого уровня статистической обработки.  
  
   В следующем примере подробно процесс приблизительное представление на программный <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метод, так как он реализован средой. Код является всего лишь примером; он не предназначен для компиляции и проверки всех ошибок был удален для ясности.  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>Код  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

