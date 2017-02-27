---
title: "Последовательность инициализации подтипы проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подтипы проектов, последовательность инициализации"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Последовательность инициализации подтипы проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Среда создает проект путем вызова базовой реализации фабрики проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>.  Разработка начинается подтипа проекта, когда среда определит, что список GUID типа проекта для расширения файла проекта не является пустым.  Идентификатор GUID модуля и проектов файла проекта определяет, является ли проект a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] OR [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] тип проекта.  Например, расширение vbproj и} {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F определяет a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] этот проект.  
  
## Инициализация среды подтипов проекта  
 Следующие сведения процедуры последовательность инициализации для системы проектов выполнить статистическое вычисление несколькими подтипами проекта.  
  
1.  Среда вызывает базовый проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>когда проект и анализирует его файл проекта он обнаруживает, что aggregate список GUID типа проекта нет  `null`.  Проект работа непосредственно создать свой проект.  
  
2.  Вызовы проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> на  `QueryService` служба для создания подтип, используя реализацию интерфейса среды проекта  <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> метод.  В рамках этого метода среды совершает рекурсивные вызовы функций в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> "  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>и  `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` методы пока он переходит список GUID типа проекта, начиная с самой внешней подтипом данного проекта.  
  
     Шаги инициализации следующие сведения.  
  
    1.  Реализация среды  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> вызовы метода  `HrCreateInnerProj```метод следующим объявлением.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Эта функция вызывается, когда впервые, т е для внешней подтипа, параметры проекта `pOuter` и  `pOwner` передайте в качестве  `null` и функция задает внешней подтип проекта  `IUnknown` В  `pOuter`.  
  
    2.  Далее вызовы среды `HrCreateInnerProj` функция со вторым идентификатором GUID типа проекта в списке.  Это идентификатор GUID \- второму внутреннее подвиду пошагового выполнения внутри проекта к базовому проект в последовательности.  
  
    3.  `pOuter` теперь указывает на  `IUnknown` внешней подтипа проекта и  `HrCreateInnerProj` вызывается реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> после вызова реализации  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>.  IN <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> управление передается в метод  `IUnknown` внешней подтипа проекта  `pOuter`.  Имеемому проект \(внутренний подтип проекта\) необходимо создать его aggregate объект проекта.  в <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> реализация метода передается в указатель на  `IUnknown` внутреннее проекта, для выполнения статистического вычисления.  Эти 2 метода создают объект статистической обработки, и в реализации должны удовлетворять правилам для статистической обработки модели COM обеспечить подтип проекта не перемещается обеспечение безопасности счетчика ссылок на себя.  
  
    4.  `HrCreateInnerProj` вызывается реализация  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>.  В этом методе подтип проекта выполняет свою работу инициализации.  Можно, например, регистрация событий в решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj` вызывается рекурсивно до тех пор, пока не будет достигнут последний идентификатор GUID \(базовый проект\) в списке.  Для каждого из этих вызовов, повторенны шаги, c через d.  `pOuter` указывает на внешней подвиду проекта  `IUnknown` для каждого уровня статистической обработки.  
  
 В следующих сведениях о приблизительном представлении в примере программный процесс <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метод как он реализован средой.  Код просто примере. он не предназначен для компилированным и вся проверка ошибок была удалена для наглядности.  
  
## Пример  
  
### Код  
  
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
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)