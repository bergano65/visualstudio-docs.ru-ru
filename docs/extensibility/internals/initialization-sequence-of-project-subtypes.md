---
title: Последовательность инициализации подтипов проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678f704c73a39cdf2130d36fcfb1a74925dd89d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726875"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Инициализация последовательности подтипов проекта
Среда конструирует проект, вызывая базовую реализацию фабрики проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Построение подтипа проекта начинается, когда среда определяет, что список GUID типа проекта для расширения файла проекта не является пустым. Расширение файла проекта и идентификатор GUID проекта указывают, является ли проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] типом проекта. Например, расширение VBPROJ и {F184B08F-C81C-45F6-A57F-5ABD9991F28F} обозначают проект [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].

## <a name="environments-initialization-of-project-subtypes"></a>Инициализация подтипов проекта в среде
 Следующая процедура содержит сведения о последовательности инициализации для системы проекта, агрегированной по нескольким подтипам проектов.

1. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> базового проекта, и пока проект анализирует свой файл проекта, он обнаруживает, что список идентификаторов GUID типа проекта не `null`. Проект прекращает работу непосредственно с созданием своего проекта.

2. Проект вызывает `QueryService` в службе <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> для создания подтипа проекта с помощью реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> в среде. В этом методе среда выполняет рекурсивные вызовы функций к реализациям методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> во время прохода по списку идентификаторов GUID типа проекта, начиная с самого внешнего подтипа проекта.

     Ниже описаны этапы инициализации.

    1. Реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> в среде вызывает метод `HrCreateInnerProj` со следующим объявлением функции:

         \<CodeContentPlaceHolder > 0 </CodeContentPlaceHolder>

         При первом вызове этой функции, то есть для самого внешнего подтипа проекта, параметры `pOuter` и `pOwner` передаются как `null`, а функция устанавливает для самого внешнего подтипа проекта `IUnknown` `pOuter`.

    2. Далее среда вызывает функцию `HrCreateInnerProj` с вторым типом проекта GUID в списке. Этот идентификатор GUID соответствует второму внутреннему подтипу проекта, пошаговым в направлении к базовому проекту в последовательности агрегирования.

    3. Теперь `pOuter` указывает на `IUnknown` самого внешнего подтипа проекта, а `HrCreateInnerProj` вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, за которой следует вызов реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> метод, который передается в `IUnknown` управления для самого внешнего подтипа проекта, `pOuter`. Собственный проект (внутренний подтип проекта) должен создавать его статистический объект проекта. В реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> передается указатель на `IUnknown` внутреннего проекта, для которого выполняется статистическая обработка. Эти два метода создают объект статистической обработки, и реализации должны следовать правилам агрегирования COM, чтобы гарантировать, что подтип проекта не удерживает счетчик ссылок самому себе.

    4. `HrCreateInnerProj` вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. В этом методе подтип проекта выполняет свою инициализацию. Например, можно зарегистрировать события решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5. `HrCreateInnerProj` вызывается рекурсивно до тех пор, пока не будет достигнут последний идентификатор GUID (базовый проект) в списке. Для каждого из этих вызовов шаги с c по d повторяются. `pOuter` указывает на самый внешний подтип проекта `IUnknown` для каждого уровня агрегирования.

## <a name="example"></a>Пример

В следующем примере подробно описан программный процесс в приблизительном представлении метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>, как он реализуется средой. Код является всего лишь примером; Он не предназначен для компиляции, и вся проверка ошибок была удалена для ясности.

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