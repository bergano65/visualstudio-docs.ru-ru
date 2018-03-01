---
title: "Управление загрузкой проекта в решении | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
Решения Visual Studio может содержать много проектов. По умолчанию Visual Studio выполняется для загрузки всех проектов в решении во время открытия решения и не разрешает пользователю доступ к любой из проектов, пока все из них завершена загрузка. Если процесс загрузки проекта будет last более двух минут, отображается индикатор хода выполнения, в число проектов, загруженных и общее количество проектов. Пользователь может выгрузить проекты во время работы в решении с несколькими проектами, но эта процедура имеет некоторые недостатки: выгруженные проекты не создаются как часть команды Перестроить решение и закрытие IntelliSense описания типов и членов проекты не отображаются.  
  
 Разработчики могут сократить время загрузки решения и управление проектом, поведение при загрузке, создав диспетчер загрузки решения. Диспетчер загрузки решения можно задавать другой проект, загрузка приоритетов для конкретных проектов или типы проектов, убедитесь, что проекты будут загружены до запуска фоновой сборки, задержка фоновой загрузки, пока не будут завершены другие фоновые задачи и выполнять другие задачи управления загрузки проекта.  
  
## <a name="project-loading-priorities"></a>Загрузка приоритеты проектов  
 Visual Studio определяет приоритеты загрузки четыре различных проекта:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(по умолчанию): при открытии решения, проекты загружаются асинхронно. Если этот приоритет имеет значение выгруженный проект после решение уже открыто, проект будут загружены в следующей точке простоя.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: при открытии решения, проекты загружаются в фоновом режиме, предоставляя пользователю возможность доступа к проектам, как они загружаются без необходимости подождать, пока загружаются все проекты.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты загружаются в том случае, когда они доступны. Проект осуществляется в том случае, когда пользователь разворачивает узел проекта в обозревателе решений, при открытии файла, принадлежащего проект при открытии решения, так как он находится в список открытых документов (находящегося в файле пользовательских параметров решения), или если другой проект то есть загружаемых имеет зависимость от проекта. Этот тип проекта не загружается автоматически перед запуском процесса построения; Диспетчер загрузки решений отвечает за гарантирует, что загружены все необходимые проекты. Эти проекты должны загружаться перед запуском поиск и замена в файлах по всему решению.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты могут не быть загружены, если пользователь явно запрашивает такое. Это случается, когда проекты, явно выгружен.  
  
## <a name="creating-a-solution-load-manager"></a>Создание диспетчера загрузки решения  
 Разработчики могут создавать загрузки решения manager путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> и предупреждающее Visual Studio о том, что диспетчер загрузки решения активен.  
  
#### <a name="activating-a-solution-load-manager"></a>Активация руководителем нагрузки решения  
 Visual Studio позволяет только один диспетчер загрузки решения в момент времени, необходимо сообщить Visual Studio, если вы хотите активировать решение нагрузки manager. Если второй диспетчер загрузки решения активирована позже, диспетчер нагрузки вашего решения будет отключен.  
  
 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> и задайте для <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойства:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Реализация IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Метод вызывается в процессе открытия решения. Для реализации этого метода используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> службы для задания приоритета нагрузки для типа проекта, вы хотите управлять. Например следующий код задает типы проектов C# для загрузки в фоновом режиме.  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Метод вызывается, если выполняется завершение работы Visual Studio или другой пакет взял на себя как диспетчер загрузки активного решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> с <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойство.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Диспетчер загрузки стратегии для различных типов решений  
 Можно реализовать диспетчеры загрузки решения по-разному в зависимости от типов решений, которые они предназначены для управления.  
  
 Диспетчер нагрузки решения предназначена для управления решения в целом загрузки, он может быть реализован как часть пакета VSPackage. Пакет должен задать для автозагрузки (AutoLoad), добавив <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> в VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Диспетчер загрузки решения, затем может быть активирован в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
> [!NOTE]
>  Дополнительные сведения о пакетах Автозагрузка см. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
 Поскольку Visual Studio распознает только последний диспетчер нагрузки решения, необходимо активировать, диспетчеры нагрузки общее решение всегда должен определить, существует ли существующий диспетчер нагрузки перед активацией сами. Если вызов GetProperty() службу решения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> возвращает `null`, отсутствует диспетчер загрузки активного решения. Если он не возвращает значение null, проверьте, является ли объект таким же, как диспетчер нагрузки вашего решения.  
  
 Если диспетчер нагрузки решения предназначена для управления лишь несколько типов решений, пакет VSPackage можно подписаться на события загрузки решения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> для активации диспетчера загрузки решения.  
  
 Если диспетчер нагрузки решения предназначена для управления только конкретные решения, сведений об активации могут сохраняться как часть файла решения. Чтобы сделать это, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительного решения.  
  
 Диспетчеры загрузки конкретного решения следует отключить сами в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчика событий, чтобы не конфликтуют с другими диспетчерами загрузки решения.  
  
 При необходимости диспетчер нагрузки решение только для сохранения приоритеты нагрузки глобального проекта (например, свойства, заданные на странице Параметры), вы можете активировать диспетчера загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> обработчика событий параметр в свойства решения, затем сохранить Отключение диспетчера загрузки решения.  
  
## <a name="handling-solution-load-events"></a>Обработка событий загрузки решения  
 Чтобы подписаться на события загрузки решения, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> после активации диспетчер нагрузки вашего решения. Если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, может отвечать на события, относящиеся к загрузке приоритеты другого проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Это возникает перед открытием решения. Его можно использовать для изменения проекта, загрузка приоритет для проектов в решении.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Это возникает после полной загрузки решения, но перед фоновая загрузка проектов начинается снова. Например пользователь мог получить проект с приоритетом нагрузки, LoadIfNeeded или диспетчер нагрузки решения мог изменить приоритет загрузки проекта для BackgroundLoad, для которого будет начинаться нагрузки фона данного проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Это создается после решения изначально полностью загружен, независимо от наличия отсутствует диспетчер загрузки решения. Она также возникает после загрузки фона или запросу загрузить каждый раз, когда оно становится полной загрузки. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> повторной активации.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Это запускается перед загрузкой проекта (или проектов). Чтобы убедиться, что другие фоновые процессы выполняются перед загрузкой проектов, задайте `pfShouldDelayLoadToNextIdle` для **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это возникает, когда пакет проектов — будут загружены. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны быть загружены в фоновом режиме; Если `fIsBackgroundIdleBatch` имеет значение false, проекты могут быть загружены синхронно, в результате запроса пользователя, например если пользователь разворачивает ожидающие проекта в обозревателе решений. Это можно реализовать для выполнения ресурсоемких операций, в противном случае пришлось бы сделать в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это возникает после загрузки пакета проектов.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Обнаружение и управление решения и проекта загрузки  
 Чтобы определить состояние загрузки проектов и решений, вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` решение и все его проекты загружаются, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакет проектов в настоящее время загружаются в фоновом режиме, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакета проектов в настоящее время загружаются синхронно в результате пользовательской команды или других явной загрузки, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` возвращает `true` Если решение в данный момент закрывается, в противном случае `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` возвращает `true` Если решение в данный момент открыт, в противном случае `false`.  
  
 Также можно обеспечить загрузку проекты и решения (независимо от нагрузки приоритеты проекта), путем вызова одного из следующих методов:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: вызов этого метода заставляет проектов в решении для загрузки перед возвратом метода.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: вызов этого метода заставляет проектов в `guidProject` для загрузки перед возвратом метода.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: вызов этого метода приводит к проекту в `guidProjectID` для загрузки перед возвратом метода.  
  
> [!NOTE]
>  . По умолчанию загружаются только проекты, которые имеют спроса и фона нагрузки приоритеты загружены, но если <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> флаг передается в метод, за исключением тех, которым явно помечены будут загружены все проекты.