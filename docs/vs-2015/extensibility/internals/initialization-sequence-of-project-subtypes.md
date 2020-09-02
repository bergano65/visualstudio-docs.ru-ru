---
title: Последовательность инициализации подтипов проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5594d54c188c2f561dd66229e808e48068ba41a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192653"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Инициализация последовательности подтипов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Среда конструирует проект, вызывая базовую реализацию фабрики проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Построение подтипа проекта начинается, когда среда определяет, что список GUID типа проекта для расширения файла проекта не является пустым. Расширение файла проекта и идентификатор GUID проекта указывают, является ли проект [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] типом проекта или. Например, расширение VBPROJ и {F184B08F-C81C-45F6-A57F-5ABD9991F28F} указывают [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] проект.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Инициализация подтипов проекта в среде  
 Следующая процедура содержит сведения о последовательности инициализации для системы проекта, агрегированной по нескольким подтипам проектов.  
  
1. Среда вызывает базовый проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , и, пока проект анализирует свой файл проекта, он обнаруживает, что список идентификаторов GUID типа агрегатного проекта не является `null` . Проект прекращает работу непосредственно с созданием своего проекта.  
  
2. Проект вызывает `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> службу для создания подтипа проекта с помощью реализации метода в среде <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . В этом методе среда выполняет рекурсивные вызовы функций к реализациям <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` методов и, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> пока он пробирает список идентификаторов GUID типа проекта, начиная с самого внешнего подтипа проекта.  
  
    Ниже описаны этапы инициализации.  
  
   1. Реализация метода в среде <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> вызывает метод "хркреатеиннерпрож" "с помощью следующего объявления функции:  
  
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
  
        При первом вызове этой функции, то есть для самого внешнего подтипа проекта, параметры `pOuter` и `pOwner` передаются как, `null` а функция задает для самого внешнего подтипа проекта `IUnknown` значение `pOuter` .  
  
   2. Затем среда вызывает `HrCreateInnerProj` функцию с вторым типом проекта GUID в списке. Этот идентификатор GUID соответствует второму внутреннему подтипу проекта, пошаговым в направлении к базовому проекту в последовательности агрегирования.  
  
   3. `pOuter`Теперь указывает на `IUnknown` внешний подтип проекта и `HrCreateInnerProj` вызывает реализацию, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> за которой следует вызов реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> методе вы передаете управление `IUnknown` внешним подтипом проекта, `pOuter` . Собственный проект (внутренний подтип проекта) должен создавать его статистический объект проекта. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> реализации метода передается указатель на элемент `IUnknown` внутреннего проекта, для которого выполняется статистическая обработка. Эти два метода создают объект статистической обработки, и реализации должны следовать правилам агрегирования COM, чтобы гарантировать, что подтип проекта не удерживает счетчик ссылок самому себе.  
  
   4. `HrCreateInnerProj` вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . В этом методе подтип проекта выполняет свою инициализацию. Например, можно зарегистрировать события решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .  
  
   5. `HrCreateInnerProj` вызывается рекурсивно до тех пор, пока не будет достигнут последний идентификатор GUID (базовый проект) в списке. Для каждого из этих вызовов шаги с c по d повторяются. `pOuter` Указывает на внешний подтип проекта `IUnknown` для каждого уровня агрегирования.  
  
   В следующем примере подробно описан программный процесс в приближенном представлении <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метода, как оно реализовано в среде. Код является всего лишь примером; Он не предназначен для компиляции, и для ясности была удалена вся проверка ошибок.  
  
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
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)
