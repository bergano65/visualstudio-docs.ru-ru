---
title: Управление загрузкой проекта в решении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ce2f80aa50c3222797d925a888e5c004b21512d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989782"
---
# <a name="managing-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Решения Visual Studio может содержать большое количество проектов. Visual Studio по умолчанию задается для загрузки всех проектов в решении во время открытия решения и не разрешает пользователю доступ к любой из проектов, пока все они завершения загрузки. Когда процесс загрузки проекта хватит на более чем за две минуты, отображается индикатор хода выполнения, в число проектов, загруженных и общее число проектов. Пользователь может выгрузить проекты при работе в решении с несколькими проектами, но эта процедура имеет определенные недостатки: выгруженные проекты не были собраны как часть команды Перестроить решение и закрытия IntelliSense описания типов и членов проекты не отображаются.  
  
 Разработчики могут сократить время загрузки решений и управление проектом, режим загрузки, создав диспетчер загрузки решения. Диспетчер загрузки решения можно задать другой проект, загрузка приоритеты для конкретных проектов или типов проектов, убедитесь, что проекты загружаются перед началом построения фона, задержка фоновой загрузки до завершения других фоновых задач и выполнения другие задачи управления загрузки проекта.  
  
## <a name="project-loading-priorities"></a>Загрузка приоритетов проектов  
 Visual Studio определяет приоритеты загрузки четыре различных проекта:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (по умолчанию): при открытии решения, проекты загружаются асинхронно. Если этот приоритет имеет значение на незагруженный проект после решение уже открыто, проект будет загружен в следующей точке простоя.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: при открытии решения, проекты загружаются в фоновом режиме, позволяя пользователю доступа к проектам, так как они загружаются без необходимости ждать, пока все проекты загружены.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты загружаются в том случае, когда они доступны. Проект осуществляется в том случае, когда пользователь разворачивает узел проекта в обозревателе решений при открытии файла, относящихся к проекту при открытии решения, так как он находится в список открытых документов (находящегося в файле пользовательских параметров решения) или другой проект то есть загрузки имеет зависимость от проекта. Этот тип проекта не загружается автоматически перед запуском процесса построения; Диспетчер загрузки решения несет ответственность за то, что все необходимые проекты были загружены. Эти проекты также должны загружаться перед началом поиска и замены в файлах по всему решению.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты могут не быть загружены, если пользователь явно запрашивает такое. Это происходит, когда проекты находятся выгружен явным образом.  
  
## <a name="creating-a-solution-load-manager"></a>Создание диспетчера загрузки решения  
 Разработчики могут создавать загрузки решения диспетчера путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> встречалась Visual Studio, что диспетчер загрузки решения активен.  
  
#### <a name="activating-a-solution-load-manager"></a>Активация диспетчер загрузки решения  
 Visual Studio позволяет только один диспетчер загрузки решения в определенный момент времени, поэтому необходимо сообщить Visual Studio, если вы хотите активировать решение нагрузки manager. Если второй диспетчер загрузки решения активирована позже, ваш диспетчер загрузки решения будет отключена.  
  
 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> службы и задать <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойства:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Реализация IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Метод вызывается в процессе открытия решения. Для реализации этого метода используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> службу, чтобы задать приоритет загрузки для типа проекта, вы хотите управлять. Например следующий код задает типы проектов C# для загрузки в фоновом режиме:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Метод вызывается, когда Visual Studio завершает работу, или когда другой пакет взял на себя как диспетчер загрузки решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> с <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойство.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Стратегии для различных видов диспетчер загрузки решения  
 Диспетчеры загрузки решения можно реализовать различными способами, в зависимости от типов используемых решений, в которой он предназначен для управления.  
  
 Если диспетчер загрузки решения предназначен для управления решения, загрузка в целом, его можно реализовать как часть пакета VSPackage. Пакета должно быть присвоено автозагрузки, добавив <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> в VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Диспетчер загрузки решения может быть активизирована в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
> [!NOTE]
>  Дополнительные сведения о Автозагрузка пакетов, см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
 Так как Visual Studio распознает только последние диспетчер загрузки решения, которое необходимо активировать, диспетчеры нагрузки общие решения всегда должен определить, существует ли существующий диспетчер нагрузки перед активацией сами. Если вызов GetProperty() службы решения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> возвращает `null`, отсутствует диспетчер нагрузки активного решения. Если он не возвращает значение null, проверьте, является ли объект так же, как ваш диспетчер загрузки решения.  
  
 Если диспетчер загрузки решения предназначена для управления только несколько типов решений, VSPackage может подписаться на события загрузки решения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> активировать диспетчер загрузки решения.  
  
 Если диспетчер загрузки решения предназначен для управления только определенные решения, информацию об активации могут быть сохранены как часть файла решения. Чтобы сделать это, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительного решения.  
  
 Диспетчеры загрузки конкретного решения следует деактивировать сами в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчик событий, чтобы не конфликтуют с другими диспетчерами загрузки решения.  
  
 Если необходимо, чтобы диспетчер загрузки решения только для сохранения приоритеты загрузки глобальных проектов (например, свойства, заданные на странице Параметры), вы можете активировать диспетчер загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> обработчик событий, сохранения параметра в свойствах решения, затем Отключите диспетчер загрузки решения.  
  
## <a name="handling-solution-load-events"></a>Обработка событий загрузки решения  
 Чтобы подписаться на события при загрузке решения, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> после активации ваш диспетчер загрузки решения. Если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, может отвечать на события, относящиеся к другому проекту, загрузка приоритеты.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Этот код выполняется до открытия решения. Его можно использовать для изменения проекта, загрузка приоритет для проектов в решении.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Этот код выполняется после полной загрузки решения, но перед фоновой загрузка проектов начинается снова. Например пользователь возможно входил в проекте с приоритетом нагрузки, LoadIfNeeded или диспетчер загрузки решения может измениться приоритет загрузки проекта, чтобы BackgroundLoad, который бы запуск фоновой загрузки этого проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Этот код выполняется после изначально полностью загружено решение, ли имеется диспетчер загрузки решения. Она также возникает после загрузки фона или запросу загрузки всякий раз, когда оно становится полностью загружен. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> повторной активации.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Этот код выполняется перед загрузкой проекта (или проектов). Чтобы убедиться, что другие фоновые процессы завершены перед загрузкой проектов, задайте `pfShouldDelayLoadToNextIdle` для **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это возникает, когда данный пакет проекты будут загружены. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны быть загружены в фоновом режиме; Если `fIsBackgroundIdleBatch` имеет значение false, проекты должны быть загружены синхронно, в результате запроса пользователя, например при развертывании проекта в обозревателе решений. Это можно реализовать для выполнения ресурсоемких работы, в противном случае будет необходимо выполнить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Этот код выполняется после загрузки пакета проектов.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Обнаружение и управление решением и загрузкой проекта  
 Чтобы обнаружить состояние загрузки проектов и решений, вызывается <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если решение и все его проекты загружаются, в противном случае `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакета проектов в настоящее время загружаются в фоновом режиме, в противном случае `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает `true` Если пакета проектов в настоящее время загружаются синхронно в результате пользовательской команды или других явную загрузку, в противном случае `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` возвращает `true` если оно в данный момент закрывается, в противном случае `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` возвращает `true` Если решение сейчас открыт, в противном случае `false`.  
  
  Также можно обеспечить загрузку проектов и решений (независимо от того, каковы приоритеты загрузки проекта), путем вызова одного из следующих методов:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: этот метод приводит проектов в решении для загрузки перед возвращением метода.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: этот метод приводит проектов в `guidProject` для загрузки перед возвращением метода.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: этот метод приводит к проекту в `guidProjectID` для загрузки перед возвращением метода.  
  
> [!NOTE]
>  . По умолчанию загружаются только проекты, которые имеют по требованию и приоритеты загрузки в фоновом режиме загружаются, но если <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> флаг передается в метод, за исключением тех, которые помечены для загрузки явно будут загружены все проекты.
