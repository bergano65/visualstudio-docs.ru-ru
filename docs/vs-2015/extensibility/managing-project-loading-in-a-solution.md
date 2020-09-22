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
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842453"
---
# <a name="managing-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Решения Visual Studio могут содержать большое количество проектов. Поведение Visual Studio по умолчанию — загружать все проекты в решении во время открытия решения, а не разрешать пользователю обращаться к каким-либо проектам до завершения загрузки всех этих проектов. Когда процесс загрузки проекта будет более двух минут, отображается индикатор выполнения, отображающий количество загруженных проектов и общее число проектов. Пользователь может выгружать проекты при работе в решении с несколькими проектами, но эта процедура имеет некоторые недостатки: выгруженные проекты не строятся в составе команды Rebuild Solution, а описания IntelliSense типов и членов закрытых проектов не отображаются.  
  
 Разработчики могут сократить время загрузки решения и управлять поведением загрузки проекта, создав диспетчер загрузки решения. Диспетчер загрузки решения может устанавливать разные приоритеты загрузки проекта для конкретных проектов или типов проектов, а также загружать проекты перед запуском фоновой сборки, задерживать фоновую загрузку до завершения других фоновых задач и выполнять другие задачи по управлению загрузкой проекта.  
  
## <a name="project-loading-priorities"></a>Приоритеты загрузки проекта  
 Visual Studio определяет четыре разных приоритета загрузки проекта:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (по умолчанию): при открытии решения проекты загружаются асинхронно. Если этот приоритет установлен для выгруженного проекта после того, как решение уже открыто, проект будет загружен в следующую точку простоя.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: при открытии решения проекты загружаются в фоновом режиме, что позволяет пользователю получить доступ к проектам по мере их загрузки без ожидания загрузки всех проектов.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты загружаются при обращении к ним. Доступ к проекту осуществляется, когда пользователь развертывает узел проекта в обозреватель решений, если файл, принадлежащий проекту, открывается при открытии решения, поскольку он находится в списке открытых документов (сохраненном в файле параметров пользователя решения) или если другой загружаемый проект имеет зависимость от проекта. Этот тип проекта не загружается автоматически перед запуском процесса сборки. Диспетчер загрузки решения отвечает за обеспечение загрузки всех необходимых проектов. Эти проекты также должны быть загружены перед началом поиска/замены в файлах во всем решении.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: проекты не должны загружаться, если пользователь явно не запрашивает их. Это происходит при явной выгрузке проектов.  
  
## <a name="creating-a-solution-load-manager"></a>Создание диспетчера загрузки решения  
 Разработчики могут создать диспетчер загрузки решения, реализовав и предприняв <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Visual Studio, что диспетчер загрузки решения активен.  
  
#### <a name="activating-a-solution-load-manager"></a>Активация диспетчера загрузки решения  
 Visual Studio допускает только один диспетчер загрузки решения в определенный момент времени, поэтому необходимо рекомендовать Visual Studio, если нужно активировать Диспетчер загрузки решения. Если второй диспетчер загрузки решения будет активирован позже, диспетчер загрузки решения будет отключен.  
  
 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> службу и задать <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойство:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Реализация Ивссолутионлоадманажер  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>Метод вызывается в процессе открытия решения. Чтобы реализовать этот метод, используйте службу, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> чтобы задать приоритет загрузки для типа проекта, которым вы хотите управлять. Например, следующий код задает типы проектов C# для загрузки в фоновом режиме:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Метод вызывается либо при завершении работы Visual Studio, либо при переходе другого пакета в качестве активного диспетчера загрузки решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> со <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> свойством.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Стратегии для различных типов диспетчера нагрузки решений  
 Вы можете реализовать диспетчеры загрузки решений различными способами в зависимости от типов решений, которыми они предназначены для управления.  
  
 Если диспетчер нагрузки решения предназначен для управления загрузкой решения в целом, его можно реализовать как часть VSPackage. Для пакета необходимо задать значение автозагрузки, добавив в <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Диспетчер загрузки решения может быть активирован в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> методе.  
  
> [!NOTE]
> Дополнительные сведения о пакетах автозагрузки см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
 Поскольку Visual Studio распознает только последний диспетчер загрузки решения, который должен быть активирован, общие диспетчеры загрузки решений всегда должны определять наличие существующего диспетчера, прежде чем активировать его. При вызове метода Property () в службе решения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> возврата отсутствует `null` активный диспетчер нагрузки решения. Если он не возвращает значение null, проверьте, совпадает ли объект с диспетчером загрузки решения.  
  
 Если диспетчер загрузки решения предназначен для управления только решениями нескольких типов, пакет VSPackage может подписываться на события загрузки решения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> активации диспетчера загрузки решения.  
  
 Если диспетчер нагрузки решения предназначен для управления только конкретными решениями, то сведения об активации можно сохранить как часть файла решения. Для этого вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительного решения.  
  
 Определенные диспетчеры загрузок решений должны деактивироваться в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчике событий, чтобы не конфликтовать с другими диспетчерами загрузки решений.  
  
 Если необходимо, чтобы диспетчер загрузки решений сохранял только приоритеты загрузки глобальных проектов (например, свойства, заданные на странице параметров), можно активировать Диспетчер загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> обработчике событий, сохранить параметр в свойствах решения, а затем отключить диспетчер загрузки решения.  
  
## <a name="handling-solution-load-events"></a>Обработка событий загрузки решения  
 Чтобы подписываться на события загрузки решения, вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> при активации диспетчера загрузки решения. При реализации можно <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> реагировать на события, связанные с различными приоритетами загрузки проекта.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Это срабатывает перед открытием решения. Его можно использовать для изменения приоритета загрузки проекта для проектов в решении.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>. Это происходит после полной загрузки решения, но до начала фоновой загрузки проекта. Например, пользователь мог получить доступ к проекту, приоритет нагрузки которого — Лоадифнидед, или диспетчеру загрузки решения изменился приоритет загрузки проекта на Баккграундлоад, что приведет к запуску фоновой загрузки этого проекта.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>. Это происходит после первоначальной загрузки решения, независимо от наличия диспетчера загрузки решения. Он также срабатывает после загрузки в фоновом режиме или по требованию, когда решение становится полностью загруженным. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> активируется повторно.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Это срабатывает перед загрузкой проекта (или проектов). Чтобы обеспечить завершение других фоновых процессов до загрузки проектов, установите значение `pfShouldDelayLoadToNextIdle` **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это происходит, когда пакет проектов собирается загрузиться. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны загружаться в фоновом режиме; Если значение `fIsBackgroundIdleBatch` равно false, проекты должны загружаться синхронно в результате запроса пользователя, например, если пользователь развертывает ожидающий проект в Обозреватель решений. Это можно реализовать для дорогостоящих операций, которые в противном случае потребуется выполнить в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это происходит после загрузки пакета проектов.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Обнаружение и управление загрузкой решений и проектов  
 Чтобы определить состояние загрузки проектов и решений, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает значение `true` , если решение и все его проекты загружены; в противном случае — `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает значение `true` , если пакет проектов в данный момент загружается в фоновом режиме; в противном случае — `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` возвращает значение `true` , если пакет проектов в данный момент загружается синхронно в результате выполнения пользовательской команды или другой явной нагрузки `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` возвращает значение `true` , если решение в данный момент закрывается, в противном случае — `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` возвращает значение `true` , если решение в данный момент открыто, в противном случае — `false` .  
  
  Также можно убедиться, что проекты и решения загружены (независимо от приоритета загрузки проекта), вызвав один из следующих методов:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: вызов этого метода приводит к принудительной загрузке проектов в решении перед возвратом метода.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: вызов этого метода приводит к принудительной `guidProject` загрузке проектов в перед возвратом из метода.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: вызов этого метода приводит к принудительной `guidProjectID` загрузке проекта в перед возвратом метода.  
  
> [!NOTE]
> . По умолчанию загружаются только проекты, для которых загружена загрузка по требованию и приоритеты фоновой загрузки, но если в <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> метод передается флаг, будут загружены все проекты, за исключением тех, которые помечены для загрузки явным образом.
