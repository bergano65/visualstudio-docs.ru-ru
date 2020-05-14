---
title: 'Как: Реализация вложенных проектов Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707976"
---
# <a name="how-to-implement-nested-projects"></a>Как: Реализация вложенных проектов

При создании вложенного типа проекта необходимо реализовать несколько дополнительных шагов. Родительский проект берет на себя те же обязанности, что и решение для вложенных (детских) проектов. Родительский проект представляет собой контейнер проектов, аналогичных решению. В частности, есть несколько событий, которые должны быть подняты решением и родительскими проектами для построения иерархии вложенных проектов. Эти события описаны в следующем процессе для создания вложенных проектов.

## <a name="create-nested-projects"></a>Создание вложенных проектов

1. Интегрированная среда разработки (IDE) загружает файл проекта и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> информацию о запуске родительского проекта, вызывая интерфейс. Родительский проект создается и добавляется в решение.

    > [!NOTE]
    > На данном этапе родительский проект еще слишком рано, чтобы создать вложенный проект, поскольку родительский проект должен быть создан до создания проекта «ребенок». После этой последовательности родительский проект может применять настройки к проектам ребенка, а проекты «ребенок» могут при необходимости получить информацию от родительских проектов. Эта последовательность, если она необходима для клиентов, таких как контроль исходного кода (SCC) и **Solution Explorer**.

     Родительский проект должен <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> дождаться вызова IDE метода, прежде чем он сможет создать свой вложенный (детский) проект или проекты.

2. IDE призывает `QueryInterface` к родительскому <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>проекту для . Если этот вызов удается, IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод родителя, чтобы открыть все вложенные проекты для родительского проекта.

3. Родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> вызывает метод уведомления слушателей о том, что вложенные проекты вот-вот будут созданы. SCC, например, прислушивается к этим событиям, чтобы узнать, происходят ли шаги в процессе создания решения и проекта в порядке. Если шаги происходят не по порядку, решение может быть неправильно зарегистрировано с помощью управления исходным кодом.

4. Родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> метод или метод на каждом из своих детских проектов.

     Вы <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> перейдете `AddVirtualProject` к методу, чтобы указать, что виртуальный (вложенный) проект должен быть добавлен в окно проекта, исключен из сборки, добавлен в элемент управления исходным кодом и так далее. `VSADDVPFLAGS`позволяет контролировать видимость вложенного проекта и указывать, какая функциональность связана с ним.

     Если вы перезагрузите ранее существующий проект ребенка, в рамках которого в `AddVirtualProjectEx`файле проекта родительского проекта хранится проект GUID, родительский проект вызывает вызовы. Единственное различие `AddVirtualProject` `AddVirtualProjectEX` между `AddVirtualProjectEX` тем, что имеет параметр, позволяющий `guidProjectID` родительскому проекту <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> указать каждый экземпляр для проекта ребенка, чтобы включить и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> функционировать правильно.

     Если GUID недоступен, например, при добавлении нового вложенного проекта, решение создает его для проекта в момент его добавления к родительскому проекту. Родительский проект несет ответственность за сохранение этого проекта GUID в файле проекта. При удалении вложенного проекта GUID для этого проекта также может быть удален.

5. IDE называет <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> метод каждого детского проекта родительского проекта.

     Родительский проект `IVsParentProject` должен быть реализован, если вы хотите гнездить проекты. Но родительский проект `QueryInterface` `IVsParentProject` никогда не требует, даже если он имеет родительские проекты под ним. Решение обрабатывает вызов `IVsParentProject` и, если оно реализовано, требует `OpenChildren` создания вложенных проектов. `AddVirtualProjectEX`всегда вызывается `OpenChildren`от . Он никогда не должен вызываться родительским проектом, чтобы поддерживать события создания иерархии в порядке.

6. IDE называет <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> метод на проекте ребенка.

7. Родительский проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> вызывает метод уведомления слушателей о том, что проекты ребенка для родительского объекта были созданы.

8. IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> метод на родительский проект после того, как все детские проекты были открыты.

     Если он еще не существует, родительский проект создает GUID `CoCreateGuid`для каждого вложенного проекта, вызывая .

    > [!NOTE]
    > `CoCreateGuid`— это aPI COM, называемый при создании GUID. Для получения дополнительной `CoCreateGuid` информации, см.

     Родительский проект хранит этот GUID в своем файле проекта, чтобы получить следующий раз, когда он будет открыт в IDE. Дополнительную информацию о призвании `AddVirtualProjectEX` получить `guidProjectID` для проекта "Ребенок" можно найти на шаг 4.

9. Затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод вызывается для родительского ItemID, который по конвенции делегируется в вложенный проект. Извлекает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> свойства узла, который гнездится в проекте, который вы хотите делегировать, когда он вызывается на родительский.

     Поскольку родительские и детские проекты мгновенно программируются, на этом этапе можно настроить свойства для вложенных проектов.

    > [!NOTE]
    > Вы не только получаете контекстную информацию от вложенного проекта, но и можете спросить, есть ли у родительского проекта контекст для этого элемента, проверяя [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Таким образом, можно добавить дополнительные динамические атрибуты справки и параметры меню, характерные для отдельных вложенных проектов.

10. Иерархия построена для отображения в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> Solution **Explorer** с вызовом к методу.

     Вы передаем иерархию в `GetNestedHierarchy` среду, чтобы построить иерархию для отображения в Solution Explorer. Таким образом, решение знает, что проект существует и может управляться для построения менеджером сборки, или может позволить файлы в проекте, чтобы быть поставлены под управление исходного кода.

11. Когда все вложенные проекты для Project1 были созданы, контроль передается обратно к решению и процесс повторяется для Project2.

     Этот же процесс для создания вложенных проектов происходит для детского проекта, в который есть ребенок. В этом случае, если бы у BuildProject1, который является ребенком Проекта1, были детские проекты, они были бы созданы после BuildProject1 и до Project2. Процесс является рекурсивным и иерархия построена сверху вниз.

     Когда вложенный проект закрывается, потому что пользователь закрыл решение или `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>сам конкретный проект, называется другой метод на , . Родительский проект обертывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> к <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> методу с методами, чтобы уведомить слушателей о событиях решения, которые в настоящее время закрыты вложенные проекты.

Следующие темы касаются нескольких других концепций, которые следует учитывать при реализации вложенных проектов:

- [Рассмотрение вопросов разгрузки и перегрузки вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтр овоедело диалога AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>См. также

- [Добавление элементов в диалоговую окно Добавить новый элемент](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Файл Мастера (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
