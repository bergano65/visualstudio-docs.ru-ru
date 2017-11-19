---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2017
---
Заголовок: «упрощенный загрузки решения (LSL) | Ms.custom документы Microsoft»:»» ms.date: ms.reviewer «01/17/2017 г.»: «» ms.suite:»» ms.technology: 
  - ms.tgt_pltfrm «vs ide sdk»: «» ms.topic: «статьи» helpviewer_keywords: 
  - «Загрузить пакеты VSPackage, простое решение»
  - «Пакеты VSPackage, быстрая загрузка решения» ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1 Автор: ms.author «gregvanl»: «gregvanl» диспетчера: ghogen
---
# <a name="lightweight-solution-load-lsl"></a>Простое решение нагрузки (LSL)

## <a name="background-information-on-lsl"></a>Общие сведения о LSL

Упрощенные загрузить решение — это новая функция в VS 2017 г которого также значительно сократить время загрузки решения, позволяя быстро работать более продуктивно. При включенной LSL Visual Studio не будет загружен полностью проектов до начала работы с ними.

LSL может влиять на расширения Visual Studio. Расширения, компоненты которого зависит от проекта для загрузки может не работать или работать неправильно без выполнения следующей инструкции, изложенные в данном документе.

Дополнительные сведения о LSL по следующим ссылкам:

* [Блог нагрузки простое решение](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Вопросы? Свяжитесь с нами[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Включите параметр загрузки проектов в режиме «отложенные»

1. Закройте все открытое решение.
2. Последовательно выберите пункты **средства** > **параметр** > **проекты и решения** > **Общие** параметры страница.
3. Проверьте **нагрузки простое решение** флажок, чтобы включить параметр.

При открытии решения с приведенный выше параметр включен, интегрированной среды разработки отображается регулярного представления проектов, но проекты не загружены.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Различия между отложенной загрузки и регулярного загрузка проектов

С помощью упрощенного загрузки решения проекты не загружаются при открытии решения. Для этих «отложенные проекты» создается заглушка иерархии. В обозревателе решений показано ожидаемое представление со значками и имена проектов, никак не пользовательского интерфейса, которые некоторые или все проекты в «отложенное режим».

С LSL включен расширения можно больше не ожидать, что необходимые проекты уже полностью загружены при запуске операции. Вызывающие объекты должны проверить ли они с зависимостями от загруженных проектов. Если расширение необходимы данные из отложенного проекта, выполните следующие расширения:

1. Загрузите проекты при необходимости.
2. Используйте новую **API-интерфейсы рабочей** для получения сведений из отложенного проекта без их загрузки.

Новый **рабочую область API-интерфейсы** разрешить расширения для получения сведений, например проекте-владельце исходного файла и все исходные файлы для указанного проекта, из отложенного проекта. В некоторых случаях только ограниченный набор проектов, нужно будет загрузить. Правый параметр — баланс между частота операций, простота альтернативные подходы и производительность работы пользователя.

Все проектов и загрузке решения, касающиеся события по-прежнему запускаются в режиме LSL. Это позволяет получить правильную работу из VS компоненты, и они ведут себя так же, как при загрузке проектов. Загрузка проекта, касающиеся работы, выполняемой при решение хотя значительно снижается.

## <a name="ui-requirements-and-changes"></a>Требования пользовательского интерфейса и изменения

Элементы пользовательского интерфейса должен обрабатывать загружена и отложенные проекты как равные. Это означает, что любое действие, которое может выполняться в загруженном проекте должен быть применимым для отложенного проекты с некоторыми исключениями. В качестве вспомогательного этого имеются изменения некоторых существующих API платформы, а также введения новых интерфейсов API.

### <a name="expectations-for-ui"></a>Ожиданий для пользовательского интерфейса

1. Компоненты необходимо показать не различия в зависимости от того, если проекты будут загружены или отложенное разрешение.
2. Все вхождения или перечисления через загруженных проектов решения, должны содержать отложенная проектах.
3. Любые действия, доступные для загрузки проекта должны быть доступны для отложенного проекта.
4. Функции должны запроса на загрузку проектов, только если:
  * Нет прямого взаимодействия с пользователем с помощью функции. Не загружать проекты приоритетным прерыванием.
  * Жест «Разделе более результатов», внесенных пользователем. Ниже приведена Эта рекомендация пользовательского интерфейса.
  * Для выполнения действия можно использовать только полностью загружен проект. Используйте LSL и откройте проект API-интерфейсы по возможности и отправьте запрос функции запросом, когда отсутствует функциональные возможности.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Изменения в платформе API-интерфейсы для диска пользовательского интерфейса

1. Задать вопрос в решение, если он был открыт в режиме загрузки решения упрощенный и сколько проекты находятся в состоянии отложенного предоставляются новые интерфейсы API.
2. Новое событие предоставляется при загрузке все отложенные проекты в решении.
3. Предоставляются новые интерфейсы API попросите проекта, если она откладывается.
4. Существующие API обновлены для включения отложенная проектах, когда запрашиваются загруженных проектов.
5. Обновляются существующие API express решением является полной загрузки после открытия решения.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Инструкции по добавлению «В разделе более результатов» для компонента.

Функции, выполняющие запрос на содержимое проектов необходимо учесть влияние отложенного проектов. В некоторых случаях функции можно получить результаты запроса, их из LSL и рабочую область API-интерфейсы для отложенного проекта. В других случаях ограничения функций требуют проектов для загрузки. Оба этих ситуациях необходимо предоставить жест «Разделе более результатов», которое позволяет пользователям полной загрузки проектов и повторного запроса. Это жест включает функции для предоставления наилучшее приближение при наличии отложенных проекты при проведении пользователя позволяет получить Идеальный результат в том случае, если проекты загружаются на самом деле.

Должен быть общий алгоритм для функции:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Когда запрос выполняется с помощью одного проекта

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Когда запрос выполняется с помощью всего решения

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Изменения API

### <a name="new-api"></a>Новый интерфейс API

IVsSolution7.IsSolutionLoadDeferred (out bool отложена)

Возвращает значение true, если текущее решение был загружен в отложенном режиме. Обратите внимание, что если решение изначально был загружен в отложенном режиме, даже если все отложенные проекты находятся в конце концов, загружаются в текущем сеансе (из-за явного указания пользователя жестов или принудительной операциями), это свойство по-прежнему будут возвращать значение true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Возвращает число проектов, в настоящее время в отложенном режиме. Это свойство будет иметь значение в диапазоне [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Возвращает значение true, если иерархия проекта находится в состоянии отложенной загрузки.

__VSENUMPROJFLAGS3 со значениями EPF_DEFERRED и EPF_NOTDEFERRED

Можно передать эти флаги [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) перебора отложенное и не отложенный проектов.

### <a name="new-events"></a>Новые события

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Это событие возникает после загрузки всех отложенная проектах. На этом этапе VSPROPID_DeferredProjectCount равно 0. Обратите внимание, что данное событие не вызывается как часть загрузки решения и могут не возникать вообще в сеансе. Она активируется только при загружаются все отложенные проекты.

### <a name="changes-to-existing-api"></a>Изменения в существующих API

* Передача [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION для [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) возвращает отложенная проектах.
* Передача [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION не возвращает отложенная проектах.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) имеет значение true в решение. Отложенная проектах, обрабатываются согласно загрузке, поэтому этот контекст задается намного более ранней, чем в режиме без LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount возвращает сумму загружена и отложенные проекты.

## <a name="helpful-code-snippets"></a>Фрагменты кода полезные

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Проверьте, если решение был открыт в режиме отложенной загрузки

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Проверьте откладывается, если проект

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Загрузить проект

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Загрузить набор проектов

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Проверяет, если решение имеются отложенные проекты

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Получение подробных сведений с интерфейсами API рабочей области

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Как получить подробные сведения в решении LSL

Новые API рабочей предоставляются через IVsSolutionWorkspaceService, помогающие получить подробные сведения о решении.

Эти API можно использовать для получения текущей рабочей области, активного решения, со сведениями об управляемом командной строки, а также службе индексирования для рабочей области. Эти API-интерфейсы дальнейшей могут использовать службу индексирования, чтобы получить подробные данные, например, все исходные файлы в проекте в проекте-владельце исходного файла, все проекты, содержащиеся в текущем решении, все ссылки на P2P в проект, и т. д.

Следующие фрагменты кода демонстрируют использование API-интерфейсов рабочей области.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Получить IVsSolutionWorkspaceService изначально

>**Примечание:** только получите IVsSolutionWorkspaceService в сценариях LSL следует избегать загрузки пакета API рабочей области.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Примечание:** следующие фрагменты предполагается _solutionWorkspaceService неактивно уже инициализирован.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Получить сведения об управляемых командной строки для отложенного проекты для активной конфигурации решения

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Получение файла активного решения в LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Получить проекте-владельце исходного файла

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Получение всех исходных файлов из проекта

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Получить P2P ссылки в проекте

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Получить все проекты в решении

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Устранение неполадок

Из-за особенностей LSL является преднамеренным, что пользователи не могли видеть разницу между загружена и отложенные проекты. Это может затруднить функции разработки и тестирования.

Можно включить визуальных подсказок в пользовательском Интерфейсе для отложенного проектов следующим образом:

1. Закройте Visual Studio
2. Regedit.exe
3. Выберите HKLM
4. Файл > Загрузить куст
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Введите «VisualStudio» в качестве имени раздела
7. Задать `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Выберите HKLM\VisualStudio
9. Файл > выгрузить куст
10. Запустите Visual Studio

У вас есть дополнительные вопросы, можно подключиться к [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).






