---
title: 'Как: реализации вложенных проектов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dffef39d735b95cff01ead7087aa8b6286e39004
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33864466"
---
# <a name="how-to-implement-nested-projects"></a>Как: реализации вложенных проектов

При создании вложенного проекта типа существует, некоторые дополнительные действия, которые должны быть реализованы. Родительский проект принимает некоторые же обязанности, в которых имеются элементы решения, его проектов вложенных (дочерний). Родительский проект — это контейнер, аналогично решения проектов. В частности существует несколько событий, которые должны вызываться решением и в проектах родительского, чтобы создать иерархию вложенных проектов. Эти события описаны в следующий процесс для создания вложенных проектов.

## <a name="create-nested-projects"></a>Создание вложенных проектов

1.  Интегрированной среды разработки (IDE) загружает сведения о файле и запуска проекта родительский проект путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> интерфейса. Родительский проект создается и добавляется в решение.

    > [!NOTE]
    > На этом этапе является слишком ранним процесса родительский проект для создания вложенного проекта, поскольку родительский проект, необходимо создать перед созданием дочерних проектов. После этой последовательности родительский проект можно применить параметры к дочерних проектов, а дочерние проекты можно получить сведения из родительской проектов, при необходимости. Эта последовательность является, если он необходим для клиентов, например системы управления исходным кодом (SCC) и обозревателе решений.

     Родительский проект необходимо дождаться <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод вызывается в интегрированной среде разработки до его можно создать его вложенные (дочерние), проекта или проектов.

2.  Интегрированная среда разработки вызовы `QueryInterface` на родительский проект для <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Если этот вызов завершается успешно, вызовы IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод родительского, чтобы открыть все вложенные проекты для родительского проекта.

3.  Вызовы родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> метод для уведомления прослушивателей, вложенные проекты будут создаваться. Например, SCC, прослушивает на эти события, чтобы знать, если в порядке выполняются следующие действия, описанные в процесс создания решения и проекта. Если шаги по порядку, решение может не зарегистрирована в системе управления версиями.

4.  Вызовы родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> метода или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> метод на каждом из его дочерних проектов.

     Передать <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> для `AddVirtualProject` добавлен метод для указания, что виртуальные проект (вложенная) должны быть добавлены в окно проекта исключено из сборки, управления исходным кодом и т. д. `VSADDVPFLAGS` позволяет управлять видимостью вложенного проекта и указывают, какие функции связаны с ней.

     При перезагрузке ранее существующий дочерний проект, имеющий значение GUID, хранимое в файле проекта родительский проект, вызовы проекта родительский проект `AddVirtualProjectEx`. Единственное различие между `AddVirtualProject` и `AddVirtualProjectEX` является то, что `AddVirtualProjectEX` имеет параметр для включения родительский проект указать на экземпляр `guidProjectID` для дочернего проекта, чтобы включить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> функции правильно.

     Если есть идентификатор GUID не доступны, например при добавлении нового вложенного проекта решения создает для проекта во время он добавляется к родительскому элементу. Он отвечает родительский проект для сохранения этого проекта GUID в файле проекта. При удалении вложенного проекта, идентификатор GUID для этого проекта также будут удалены.

5.  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> метод для каждого дочернего проекта родительского проекта.

     Родительский проект должен реализовывать `IVsParentProject` Если вы хотите вкладывать друг в друга проектов. Но родительский проект никогда не вызывает `QueryInterface` для `IVsParentProject` даже при наличии родительские проекты под ним. Решение обрабатывает вызов `IVsParentProject` и, если она реализована вызывает `OpenChildren` для создания вложенных проектов. `AddVirtualProjectEX` всегда вызывается из `OpenChildren`. Он никогда не должен вызываться с родительский проект, чтобы сохранить события создания иерархии в порядке.

6.  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> метод к дочернему проекту.

7.  Вызовы родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> метод для уведомления прослушивателей, были созданы дочерние проекты для родительского элемента.

8.  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> метод на родительский проект после открытия всех дочерних проектов.

     Если он еще не существует, родительский проект создает идентификатор GUID для каждого вложенного проекта путем вызова `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` COM API, вызывается при GUID будет создано. Дополнительные сведения см. в разделе `CoCreateGuid` и идентификаторы GUID в библиотеке MSDN.

     Родительский проект сохраняет этот идентификатор GUID в файле проекта требуется извлечь при очередном открытии Интегрированной среды разработки. См. в шаге 4, Дополнительные сведения, относящиеся к вызовы `AddVirtualProjectEX` для получения `guidProjectID` для к дочернему проекту.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Затем вызывается метод для родительского ItemID по соглашению делегировать в вложенный проект. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Извлекает свойства, вложенной в проект, который нужно передать в при вызове для родительского узла.

     Поскольку родительские и дочерние проекты создаются программными средствами, можно задать свойства для вложенных проектов на этом этапе.

    > [!NOTE]
    > Не только получено контекстную информацию из вложенного проекта, но также можно задать, если родительский проект имеет любой контекст для этого элемента путем проверки <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. Таким образом можно добавить дополнительные атрибуты динамической справки и определенные параметры меню в отдельные вложенные проекты.

10. Иерархия создается для отображения в обозревателе решений с помощью вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> метод.

     Передайте иерархии в среде через `GetNestedHierarchy` Чтобы создать иерархию для отображения в обозревателе решений. Таким образом решение знает, что проект существует и может управляться с менеджером построений для построения или можно разрешить файлов в проекте, чтобы поместить в системе управления версиями.

11. После создания всех вложенных проектов для Проект1 управление передается обратно в решение и затем процесс повторяется для Project2.

     Этот процесс для создания вложенных проектов происходит для дочернего проекта, который содержит дочерний элемент. В этом случае если BuildProject1, который является потомком Project1, дочерних проектов, они будут создаваться после BuildProject1 и перед Project2. Процесс является рекурсивной и построении иерархии сверху вниз.

     При закрытии вложенного проекта, так как пользователь закрыл решения или конкретный сам проект, другой метод в `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, вызывается. Родительский проект создает оболочку для вызовов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> методы для уведомления прослушивателей событий решения закрытие вложенных проектов.

Следующие разделы имеют дело с других понятиях следует учитывать при реализации вложенных проектов:

- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>См. также

- [Добавление элементов в диалоговые окна "Добавление новых элементов"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ-файл)](../../extensibility/internals/wizard-dot-vsz-file.md)