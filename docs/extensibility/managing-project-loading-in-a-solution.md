---
title: "Управление загрузкой проекта в решении | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "решения, Управление загрузкой проекта"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Управление загрузкой проекта в решении
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Решения Visual Studio может содержать множество проектов. Visual Studio по умолчанию задается для загрузки всех проектов в решении во время открытия решения и запретить пользователю доступ к любой из проектов, пока не завершены все их загрузки. Когда процесс загрузки проекта продлится более двух минут, отображается индикатор хода выполнения, в число проектов, загруженных и общее число проектов. Пользователь может выгрузить проекты при работе в решении с несколькими проектами, но эта процедура имеет некоторые недостатки: выгруженные проекты не создаются как часть команды Перестроить решение и описаний IntelliSense, типов и членов закрытых проектов не отображаются.  
  
 Разработчики могут сократить время загрузки решения и управления проектом, режим загрузки, создав диспетчер загрузки решения. Диспетчер загрузки решения можно задать другой проект, загрузка приоритеты для конкретных проектов или типы проектов, убедитесь, что проекты будут загружены до запуска фоновой сборки, задержка фоновой загрузки, пока не будут завершены другие фоновые задачи и выполнять другие задачи управления для загрузки проекта.  
  
## Загрузка приоритетов проекта  
 Visual Studio определяет четыре приоритета загрузки другого проекта:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(по умолчанию\): при открытии решения, проекты загружаются асинхронно. Если приоритет имеет значение выгруженный проект после решение уже открыто, проект будет загружен в следующей точке простоя.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: при открытии решения, проекты загружаются в фоновом режиме, позволяя пользователю доступа к проектам, как они загружаются без необходимости ждать, пока загружаются все проекты.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты загружаются, когда они доступны. Проект осуществляется в том случае, когда пользователь разворачивает узел проекта в обозревателе решений при открытии файла, принадлежащего проект при открытии решения, так как он находится в списке открытых документов \(сохраняются в файле пользовательских параметров решения\), или если другой проект, загружаемых имеет зависимость от проекта. Этот тип проекта не загружается автоматически перед началом процесса построения; Диспетчер загрузки решения отвечает за обеспечение, что загружены все необходимые проекты. Эти проекты должны загружаться перед началом поиска и замены в файлах по всему решению.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты могут не быть загружены пока пользователь явно запрашивает ее. Это так явно выгружаются проектов.  
  
## Создание диспетчера загрузки решения  
 Разработчики могут создавать решения нагрузки manager путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> встречалась Visual Studio, что диспетчер загрузки решения активен.  
  
#### Активация диспетчер нагрузки решения  
 Visual Studio позволяет только один диспетчер загрузки решения в момент времени, необходимо сообщить Visual Studio, если вы хотите активировать решение нагрузки manager. Если второй диспетчер загрузки решения активирована позже, в диспетчере загрузки решения будут отключены.  
  
 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> и присвойте параметру <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойство:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### Реализация IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Метод вызывается в процессе открытия решения. Для реализации этого метода используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> службы для задания приоритета нагрузки для типа проекта, вы хотите управлять. Например следующий код задает типы проектов C\# для загрузки в фоновом режиме.  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Метод вызывается при завершении работы Visual Studio или при другой пакет взял на себя роль диспетчера загрузки активного решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> с <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойство.  
  
#### Стратегии для различных видов диспетчера загрузки решения  
 По\-разному в зависимости от типов решений, которые они предназначены для управления можно реализовать решение диспетчеров загрузки.  
  
 Если диспетчер нагрузки решение предназначено для управления решения в целом загрузки, он может быть реализован как часть VSPackage. Пакет должно быть присвоено автозагрузки, добавив <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> в VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Диспетчер загрузки решения может быть активизирована в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
> [!NOTE]
>  Дополнительные сведения о пакетах Автозагрузка см. в разделе [Загрузка пакетов VSPackages](../extensibility/loading-vspackages.md).  
  
 Поскольку Visual Studio распознает только последний диспетчер нагрузки решений, активировать, диспетчеры загрузки общее решение всегда должен определить, существует ли существующий диспетчер загрузки перед активацией сами. Если вызов GetProperty\(\) службы решения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> возвращает `null`, отсутствует диспетчер загрузки активного решения. Если он не возвращает значение null, проверьте, совпадает ли объект диспетчера нагрузки вашего решения.  
  
 Если диспетчер загрузки решения предназначен для управления лишь несколько типов решений, VSPackage можно подписаться на события при загрузке решения \(путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> для активации диспетчера загрузки решения.  
  
 Если диспетчер нагрузки решение предназначено для управления только определенные решения, сведений об активации могут сохраняться как часть файла решения. Чтобы сделать это, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительного решения.  
  
 Диспетчеры загрузки конкретного решения следует деактивировать сами в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчик событий, чтобы не конфликтуют с другими диспетчерами нагрузки решения.  
  
 Если необходимо, чтобы диспетчер нагрузки решение только для сохранения приоритеты нагрузки глобального проекта \(например, свойства, заданные на странице Параметры\), вы можете активировать диспетчера загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> обработчик событий сохраняются настройки свойства решения, а затем отключить диспетчер загрузки решения.  
  
## Обработка событий загрузки решения  
 Чтобы подписаться на события при загрузке решения, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> После активации в диспетчере загрузки решения. При реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, может реагировать на события, относящиеся к загрузке приоритеты другого проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Этот код выполняется перед открытием решения. Его можно использовать для изменения проекта, загрузка приоритет для проектов в решении.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Это срабатывает после полной загрузки решения, но перед фоновой загрузки проекта начинается заново. Например пользователь может обращались с приоритетом нагрузки, которая LoadIfNeeded или диспетчер загрузки решения мог изменить приоритет загрузки проекта для BackgroundLoad, который будет запуск фоновой загрузки этого проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Это срабатывает после решения изначально полностью загружен, ли имеется диспетчер нагрузки решения. Она также возникает после загрузки фона или запросу загрузки всякий раз, когда оно становится полностью загружен. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> активируется повторно.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Этот код выполняется перед загрузкой проекта \(или проекты\). Чтобы убедиться, что другие фоновые процессы будут завершены перед загрузкой проектов, задайте `pfShouldDelayLoadToNextIdle` для **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это возникает, когда пакет проектов — будут загружены. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны быть загружены в фоновом режиме; Если `fIsBackgroundIdleBatch` имеет значение false, проекты могут быть загружены синхронно, в результате запроса пользователя, например если пользователь разворачивает ожидающие проект в обозревателе решений. Это можно реализовать дорогих работы, в противном случае будет необходимо выполнить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это срабатывает после загрузки пакета проектов.  
  
## Обнаружение и управление решения и проекта загрузки  
 Чтобы определить состояние нагрузки проектов и решений, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` решение и его проекты загружаются, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакет проекты в настоящее время загружаются в фоновом режиме, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакет проекты в настоящее время загружаются синхронно в результате команды user или других явные загрузку, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` возвращает `true` Если решение в данный момент закрывается, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` возвращает `true` если в данный момент открытии решения, в противном случае `false`.  
  
 Можно также обеспечить загрузку проекты и решения \(независимо от нагрузки приоритеты проекта\), путем вызова одного из следующих методов:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: вызов этого метода заставляет проектов в решении для загрузки перед возвратом метода.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: вызов этого метода заставляет проектов в `guidProject` для загрузки перед возвратом метода.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: этот метод приводит к проекту в `guidProjectID` для загрузки перед возвратом метода.  
  
> [!NOTE]
>  . По умолчанию загружаются только проектов, имеющих требования и загружаются фоновой нагрузки приоритетов, но если <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> флаг передается в метод, за исключением тех, отмеченных как явно загрузить будут загружены все проекты.