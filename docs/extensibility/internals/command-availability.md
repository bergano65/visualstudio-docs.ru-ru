---
title: Команда доступности | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08f6ceb6c57eccf359b4aa23db7d693df3b86453
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128695"
---
# <a name="command-availability"></a>Доступность команд

Visual Studio контекст определяет, какие команды имеются. Контекст может меняться в зависимости от текущего проекта, текущий редактор, пакеты VSPackage, загружаются и другие виды интегрированной среды разработки (IDE).

## <a name="command-contexts"></a>Команда контексты

Следующие команды контексты наиболее распространены.

-   **Интегрированная среда разработки** всегда доступны команды, приведенные в Интегрированной среде разработки.

-   **VSPackage** пакеты VSPackage можно определить, когда команды, чтобы отобразить или скрыть.

-   **Проект** проекта команды отображаются только для выбранного проекта.

-   **Редактор** одновременно может быть активна только одна редактора. Доступные команды в активном редакторе. Редактор работает в тесном сотрудничестве с языковой службы. Служба языка необходимо обработать его команды в контексте связанного редактора.

-   **Тип файла** редактор можно загрузить более одного типа. Доступные команды можно изменить в зависимости от типа файла.

-   **Активное окно** последнего окна для активного документа задает контекст пользовательского интерфейса пользователя для сочетания клавиш. Однако окно инструментов, которая содержит таблицу привязки ключей похожа на внутренний веб-браузер также задать в контексте пользовательского интерфейса. Для окон документов, несколькими вкладками, таким как редактор HTML в каждой табуляции имеет другую команду контекст GUID. После регистрации окно инструментов было всегда доступным на **представление** меню.

-   **Контекст пользовательского интерфейса** контексты пользовательского интерфейса определяются по значениям <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> классов, например, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> при построении решения или <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> когда активна отладчик. Несколько контекстов пользовательского интерфейса может быть активен одновременно.

## <a name="defining-custom-context-guids"></a>Определение пользовательского контекста GUID

Если соответствующую команду контекста GUID еще не определен, можно определить ее в VSPackage и затем программировать быть активным или неактивным при необходимости для контроля видимости вашей команды.

1.  Зарегистрируйте идентификаторы GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод.

2.  Получить состояние контекста GUID, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод.

3.  Включать идентификаторы GUID контекста и отключать путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод.

    > [!CAUTION]
    > Убедитесь, что VSPackage не влияет на GUID любого существующего контекста из-за других пакетов VSPackage может зависят от них.

## <a name="see-also"></a>См. также

- [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)