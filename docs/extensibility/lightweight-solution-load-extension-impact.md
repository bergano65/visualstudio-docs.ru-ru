---
title: "Простое решение нагрузки (LSL) | Документы Microsoft"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>Простое решение нагрузки (LSL)

## <a name="background-information-on-lsl"></a>Общие сведения о LSL

Облегченная загрузить решение — это новая функция в VS 2017 г которого будет существенно снижено время загрузки решения, позволяя быстро работать более производительно. При включении LSL Visual Studio не загрузится полностью проектов до начала работы с ними.

LSL влияющих расширений Visual Studio. Расширения которого функции зависят от проекта для загрузки может не работать или работать неправильно без выполнения следующей инструкции, изложенные в данном документе.

Дополнительные сведения о LSL воспользуйтесь следующими ссылками:

* [Блог нагрузки простое решение](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Вопросы? Напишите нам по адресу[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Включите параметр для загрузки проектов в режиме «отложенные»

1. Закройте другое открытое решение.
2. Последовательно выберите пункты **средства** > **параметр** > **проекты и решения** > **Общие** параметры страницы.
3. Проверьте **нагрузки простое решение** поле, чтобы включить параметр.

При открытии решения с приведенный выше параметр включен, интегрированная среда разработки показывает регулярные представление проектов, но проектов не загружаются.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Различия между отложенной загрузки и регулярные нагрузки проектов

Загрузке облегченного решения проекты не будут загружаться при открытии решения. Для этих «отложенные проекты» создается заглушка иерархии. В обозревателе решений показано ожидаемое представление со значками и имена проектов, нет никаких признаков пользовательского интерфейса, некоторые или все проекты в «режиме отложенного».

С LSL включен расширения больше не может быть уже полностью загрузку необходимые проекты при запуске операции. Вызывающие объекты должны проверить ли они с зависимостями от загруженных проектов. Если расширение необходима информация из отложенного проекта, расширение выполните следующее:

1. При необходимости загрузите проект или проекты.
2. Использовать новый **API-интерфейсы рабочей** для получения информации из отложенного проекта без их загрузки.

Новый **API-интерфейсы рабочей** разрешить расширения получить сведения, такие как владелец проекта исходный файл и все исходные файлы для указанного проекта, из отложенного проекта. В некоторых случаях только ограниченный набор проектов, должны быть загружены. Правый параметр — баланс между частота операций, простота альтернативные подходы и общее удобство работы пользователей.

Все проектов и решений нагрузки, связанная с события по-прежнему запускаются в режиме LSL. Это позволяет компонентам для получения ожидаемого поведения из VS и ведут себя так же, как при загрузке проектов. Работа, выполняемая при открытом решении хотя значительно сокращается, касающиеся загрузки проекта.

## <a name="ui-requirements-and-changes"></a>Требования пользовательского интерфейса и изменения

Элементы пользовательского интерфейса должен обрабатывать загружена и отложенные проекты как равные. Это означает, что любое действие, которое может выполняться для загруженного проекта должен быть применимым для отложенного проектов, с некоторыми исключениями. Для выполнения этой функции, внесены изменения для некоторых существующих API платформы, а также введения новых интерфейсов API.

### <a name="expectations-for-ui"></a>Ожидания для пользовательского интерфейса

1. Функции необходимо показать без visual различия в зависимости от того, если загружаются или отложенное проектов.
2. Любых или перечисления через загрузить проекты решения должен содержать отложенное проектов.
3. Любые действия, доступные для загрузки проекта должны быть доступны для отложенного проекта.
4. Функции должны запрос на загрузку этих проектов только если:
  * Нет прямого взаимодействия с пользователем с помощью функции. Не загружать проекты заблаговременно.
  * Жест «Разделе более результаты» выполняется пользователем. Эта рекомендация пользовательского интерфейса см.
  * Только полностью загружен проект можно использовать для выполнения действия. Использовать LSL и открытые API проекта, по возможности и отправьте запрос функции запрашивает при отсутствии функциональные возможности.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Изменения в API, которое поможет движению пользовательского интерфейса платформы

1. Новые интерфейсы API, позволяющих попросите решение, если он был открыт в режиме нагрузки облегченного решения и сколько проекты находятся в состоянии отложенного.
2. Новое событие предоставляется для загрузки всех отложенных проектов в решении.
3. Новые интерфейсы API, позволяющих попросите проекта, если она откладывается.
4. Существующие API обновлены для включения отложенное проектов при запросе для загрузки проектов.
5. Обновляются существующие API express решение полностью загружена после открытия решения.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Как добавить «Разделе более результаты» для компонента.

Функции, которые выполняют запросы по содержимому проектов необходимо учесть влияние отложенного проектов. В некоторых случаях функции можно получить результаты запроса, их из рабочей области API и LSL для отложенного проекта. В других случаях ограничения функций требуют проектов для загрузки. Обе эти ситуации следует предоставить жест «Разделе более результатов», позволяющий пользователям полная загрузка проектов и повторного запроса. Этот жест включает функции для предоставления наилучшее приближение при отложенного проекты во время предоставления пользователю получить идеального результата при проекты загружаются на самом деле.

Общий алгоритм для функций должно быть:

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
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
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

IVsSolution7.IsSolutionLoadDeferred (out bool отложенное)

Возвращает значение true, если текущее решение был загружен в отложенном режиме. Обратите внимание, что если решение изначально была загружена в отложенном режиме, даже если все отложенные проекты будут в конечном счете, загружаются в текущем сеансе (из-за явных пользовательских жестов или принудительное операциями), это свойство по-прежнему будут возвращать значение true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Возвращает число проектов, в настоящее время в отложенном режиме. Это свойство будет иметь значение в диапазоне [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Возвращает значение true, если иерархия проекта находится в состоянии отложенной загрузки.

__VSENUMPROJFLAGS3 со значениями, EPF_DEFERRED и EPF_NOTDEFERRED

Можно передать эти флаги [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) для перебора отложенное и не отложенные проекты.

### <a name="new-events"></a>Новые события

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Это событие возникает после загрузки всех отложенных проектов. На этом этапе VSPROPID_DeferredProjectCount равно 0. Обратите внимание, что данное событие не вызывается в рамках решения нагрузки и могут не возникать вообще в сеансе. Только срабатывает при загружаются все отложенные проекты.

### <a name="changes-to-existing-api"></a>Изменения в существующих API

* Передача [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION для [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) возвращает отложенное проектов.
* Передача [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION не возвращает отложенное проектов.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) имеет значение true в открытом решении. Отложенное проекты, обрабатываются в процессе загрузки, поэтому этот контекст задается практически более ранней, чем в режиме без LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount возвращает сумму загружена и отложенные проекты.

## <a name="helpful-code-snippets"></a>Фрагменты кода полезно

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

### <a name="check-if-a-project-is-deferred"></a>Проверка откладывается, если проект

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Загрузка проекта

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

## <a name="getting-detailed-information-with-workspace-apis"></a>Получение подробные сведения с помощью API рабочей области

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Как получить подробные сведения для решения LSL

Новые интерфейсы API для рабочей области, предоставляются по IVsSolutionWorkspaceService, помогающие получить подробные сведения о решении.

Эти интерфейсы API можно использовать для получения текущей рабочей области, активного решения, info управляемых командной строки, а также службу индексирования для рабочей области. Эти API-интерфейсы Дополнительно можно использовать службу индексирования, чтобы получить подробные данные, например, все исходные файлы в проекте проекта-владельца файла, все проекты, содержащиеся в текущем решении, все ссылки на P2P в проект, и т. д.

Следующие фрагменты кода демонстрируют использование API-интерфейсов рабочей области.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Изначально получить IVsSolutionWorkspaceService

>**Примечание:** только получите IVsSolutionWorkspaceService в сценариях LSL следует избегать загрузки пакета рабочей области API.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Примечание:** следующие фрагменты кода предполагается _solutionWorkspaceService уже лениво инициализирован.

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

### <a name="get-the-active-solution-file-in-lsl"></a>Получите файл активного решения в LSL

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

### <a name="get-the-owning-project-of-a-source-file"></a>Получение владельца проекта исходного файла

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

### <a name="get-all-source-files-from-a-project"></a>Получить все исходные файлы из проекта

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

### <a name="get-the-p2p-references-in-a-project"></a>Получение ссылок P2P в проекте

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

### <a name="get-all-the-projects-in-a-solution"></a>Получение всех проектов в решении

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

Из-за природы LSL преднамеренно, что пользователи не могут видеть разницу между загружена и отложенные проекты. Это может затруднить функции разработки и тестирования.

Visual подсказки в пользовательском Интерфейсе для отложенного проектов можно включить следующим образом:

1. Закройте Visual Studio
2. Regedit.exe
3. Выделите HKLM
4. Файл настроек загрузить куст
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Введите в качестве имени раздела «VisualStudio»
7. Задайте `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Выберите HKLM\VisualStudio
9. Файл настроек выгрузить куст
10. Запустите Visual Studio

Все дополнительные вопросы, пожалуйста привлечь [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).







