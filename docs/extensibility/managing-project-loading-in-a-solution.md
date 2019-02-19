---
title: Управление загрузкой проекта в решении | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90a97097eed7b97ad96bfda1f5520d1a9b4f0203
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335406"
---
# <a name="manage-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
Решения Visual Studio может содержать большое количество проектов. Visual Studio по умолчанию задается для загрузки всех проектов в решении во время открытия решения и не разрешает пользователю доступ к любой из проектов, пока все они завершения загрузки. Когда процесс загрузки проекта хватит на более чем за две минуты, отображается индикатор хода выполнения, в число проектов, загруженных и общее число проектов. Пользователь может выгрузить проекты при работе в решении с несколькими проектами, но эта процедура имеет определенные недостатки: выгруженные проекты не были собраны как часть команды Перестроить решение и закрытия IntelliSense описания типов и членов проекты не отображаются.

 Разработчики могут сократить время загрузки решений и управление проектом, режим загрузки, создав диспетчер загрузки решения. Диспетчер загрузки решения можно убедитесь, что проекты загружаются перед началом построения фона, задержке фоновой загрузки до завершения других фоновых задач, а также выполнять другие задачи управления для загрузки проекта.

## <a name="create-a-solution-load-manager"></a>Создать диспетчер загрузки решения
 Разработчики могут создавать загрузки решения диспетчера путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> встречалась Visual Studio, что диспетчер загрузки решения активен.

### <a name="activate-a-solution-load-manager"></a>Активировать диспетчер загрузки решения
 Visual Studio позволяет только один диспетчер загрузки решения в определенный момент времени, поэтому необходимо сообщить Visual Studio, если вы хотите активировать решение нагрузки manager. Если второй диспетчер загрузки решения активирована позже, ваш диспетчер загрузки решения будет отключена.

 Необходимо получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> службы и задать [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) свойство:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Метод вызывается, когда Visual Studio завершает работу, или когда другой пакет взял на себя как диспетчер загрузки решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> с [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) свойство.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Стратегии для различных видов диспетчер загрузки решения
 Диспетчеры загрузки решения можно реализовать различными способами, в зависимости от типов используемых решений, в которой он предназначен для управления.

 Если диспетчер загрузки решения предназначен для управления решения, загрузка в целом, его можно реализовать как часть пакета VSPackage. Пакета должно быть присвоено автозагрузки, добавив <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> в VSPackage со значением <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Диспетчер загрузки решения может быть активизирована в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.

> [!NOTE]
>  Дополнительные сведения о Автозагрузка пакетов, см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).

 Так как Visual Studio распознает только последние диспетчер загрузки решения, которое необходимо активировать, диспетчеры нагрузки общие решения всегда должен определить, существует ли существующий диспетчер нагрузки перед активацией сами. Если вызов `GetProperty()` службу решения для [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) возвращает `null`, отсутствует диспетчер нагрузки активного решения. Если он не возвращает значение null, проверьте, является ли объект так же, как ваш диспетчер загрузки решения.

 Если диспетчер загрузки решения предназначена для управления только несколько типов решений, VSPackage может подписаться на события загрузки решения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) и использовать обработчик событий для <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> активировать диспетчер загрузки решения.

 Если диспетчер загрузки решения предназначен для управления только определенные решения, информацию об активации могут быть сохранены как часть файла решения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> для раздела предварительного решения.

 Диспетчеры загрузки конкретного решения следует деактивировать сами в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> обработчик событий, чтобы не конфликтуют с другими диспетчерами загрузки решения.

 Если необходимо, чтобы диспетчер загрузки решения только для сохранения свойств нагрузки глобальных проектов (например, свойства, заданные на странице Параметры), вы можете активировать диспетчер загрузки решения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> обработчик событий, сохранения параметра в свойствах решения, затем Отключите диспетчер загрузки решения.

## <a name="handle-solution-load-events"></a>Обработка событий загрузки решения
 Чтобы подписаться на события при загрузке решения, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> после активации ваш диспетчер загрузки решения. Если вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, может отвечать на события, относящиеся к другому проекту при загрузке свойств.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Это событие вызывается перед открытием решения.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Это событие вызывается после полной загрузки решения, но перед фоновой загрузка проектов начинается снова.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Это событие создается после изначально полностью загружено решение, ли имеется диспетчер загрузки решения. Она также возникает после загрузки фона или запросу загрузки всякий раз, когда оно становится полностью загружен. В то же время <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> повторной активации.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Это событие возникает перед загрузкой проекта (или проектов). Чтобы убедиться, что другие фоновые процессы завершены перед загрузкой проектов, задайте `pfShouldDelayLoadToNextIdle` для **true**.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это событие возникает в том случае, когда данный пакет проекты будут загружены. Если `fIsBackgroundIdleBatch` имеет значение true, проекты должны быть загружены в фоновом режиме; Если `fIsBackgroundIdleBatch` имеет значение false, проекты должны быть загружены синхронно, в результате запроса пользователя, например при развертывании проекта в обозревателе решений. Можно обработать это событие для выполнения ресурсоемких работы, в противном случае будет необходимо выполнить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это событие вызывается после загрузки пакета проектов.

## <a name="detect-and-manage-solution-and-project-loading"></a>Обнаружение и управление ими решение и загрузкой проекта
 Чтобы обнаружить состояние загрузки проектов и решений, вызывается <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> со следующими значениями:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` возвращает `true` Если решение и все его проекты загружаются, в противном случае `false`.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` возвращает `true` Если пакета проектов в данный момент загружается в фоновом режиме, в противном случае `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` возвращает `true` Если пакета проектов в данный момент загружается синхронно в результате пользовательской команды или других явную загрузку, в противном случае `false`.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` возвращает `true` если оно в данный момент закрывается, в противном случае `false`.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` возвращает `true` Если решение сейчас открыт, в противном случае `false`.

Также можно обеспечить загрузку проектов и решений, вызвав один из следующих методов:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: этот метод приводит проектов в решении для загрузки перед возвращением метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: этот метод приводит проектов в `guidProject` для загрузки перед возвращением метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: этот метод приводит к проекту в `guidProjectID` для загрузки перед возвращением метода.
