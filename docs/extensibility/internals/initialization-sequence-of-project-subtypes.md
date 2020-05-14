---
title: Последовательность инициализации подтипов проектов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707630"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Инициализация последовательности подтипов проекта
Окружающая среда строит проект, называя базовый проект завод реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Строительство подтипа проекта начинается, когда среда определяет, что список GUID типа проекта для расширения файла проекта не пуст. Расширение файла проекта и GUID проекта [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] указывают, является ли проект типом проекта или [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] типом проекта. Например, расширение .vbproj и «F184B08F-C81C-45F6-A57F-5ABD9991F28F» идентифицируют [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проект.

## <a name="environments-initialization-of-project-subtypes"></a>Инициализация подтипов проектов по окружающей среде
 Следующая процедура детализирует последовательность инициализации для проектной системы, агрегированной несколькими подтипами проекта.

1. Среда называет базовый <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>проект, и в то время как проект разбирает файл проекта, он `null`обнаруживает, что совокупный список GUID типа проекта не является. Проект прекращает непосредственное создание своего проекта.

2. Проект призывает `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> службу создать подтип проекта с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> реализации метода среды. В рамках этого метода среда делает рекурсивные вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>функции для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> методов, пока он идет список guiD типа проекта, начиная с внешнего подтипа проекта.

     Ниже приведены подробные сведения о шагах инициализации.

    1. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> метода среды вызывает `HrCreateInnerProj` метод со следующим иследующим заявлением функции:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Когда эта функция вызывается в первый раз, то есть для подтипа внешнего проекта, параметры `pOuter` и `pOwner` передаются в виде `null` и функция устанавливает внешний подтип `IUnknown` `pOuter`проекта.

    2. Далее функция `HrCreateInnerProj` вызовов среды со вторым типом проекта GUID в списке. Этот GUID соответствует второму подтипу внутреннего проекта, вступающему в базовый проект в последовательности агрегирования.

    3. В `pOuter` настоящее время `IUnknown` указывая на внешний `HrCreateInnerProj` подтип проекта, и называет вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> следуют призыв к вашей реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> методе вы проходите в `IUnknown` управлении внешним `pOuter`подтипом проекта, . Принадлежащий проект (внутренний подтип проекта) должен создать здесь свой агрегированный объект проекта. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> реализации метода вы проходите `IUnknown` в указатель на внутренний проект, который агрегируется. Эти два метода создают объект агрегации, и ваши реализации должны следовать правилам агрегации COM, чтобы гарантировать, что подтип проекта не будет в конечном итоге удерживать подсчет ссылок на себя.

    4. `HrCreateInnerProj`вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. В этом методе подтип проекта выполняет свою работу по инициализации. Вы можете, например, зарегистрировать <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>события решения в .

    5. `HrCreateInnerProj`называется рекурсивно до тех пор, пока не будет достигнут последний GUID (базовый проект). Для каждого из этих вызовов, шаги, c через d, повторяются. `pOuter`указывает на внешний подтип `IUnknown` проекта для каждого уровня агрегации.

## <a name="example"></a>Пример

В следующем примере описывается программный процесс <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> в приблизительном представлении метода, как он реализуется средой. Код является лишь примером; он не предназначен для компилирования, и все проверки ошибок были удалены для ясности.

```cpp
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

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)
