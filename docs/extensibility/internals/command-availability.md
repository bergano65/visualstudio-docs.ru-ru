---
title: Команда доступности | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5087e5f7958f9abe46e0caeb2eb03e21285e4da7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338592"
---
# <a name="command-availability"></a>Доступность команд

Контекст Visual Studio определяет, какие команды доступны. Контекст может меняться в зависимости от текущего проекта, текущий редактор, пакеты VSPackage, который загружаются и другие аспекты интегрированной среде разработки (IDE).

## <a name="command-contexts"></a>Командных контекстов

Следующие команды контексты являются наиболее частыми:

- В ИНТЕГРИРОВАННОЙ СРЕДЕ РАЗРАБОТКИ: Команды, предоставляемые IDE всегда доступны.

- VSPackage: Пакеты VSPackage можно определить, когда команды, чтобы отобразить или скрыть.

- Проект: Команды проекта отображаются только текущий выбранный проект.

- Редактор: Одновременно может быть active только одного редактора. Команды из активного редактора доступны. Редактор тесно сотрудничает с языковой службой. Служба языка необходимо обработать его команды в контексте связанного редактора.

- Тип файла: Редактор можно загрузить более одного типа. Доступные команды могут меняться в зависимости от типа файла.

- Активное окно: Последнего активного документа окна задает контекст пользовательского интерфейса пользователя для сочетания клавиш. Тем не менее окно инструментов, которая содержит таблицу привязки ключей, похожий на внутренний веб-браузер можно также задать контекст пользовательского интерфейса. Для окон документов, с несколькими вкладками, такие как редактор HTML Каждая вкладка имеет другую команду контекст GUID. После регистрации окна инструментов, он всегда был доступен на **представление** меню.

- UI context: Контексты пользовательского интерфейса определяются по значениям <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> класса, например, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> при сборке решения или <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> когда отладчик активен. Несколько контекстов пользовательского интерфейса может быть активен в то же время.

## <a name="define-custom-context-guids"></a>Определение пользовательских контекстные GUID

Если контекст соответствующей команды, которые уже не определен идентификатор GUID, можно определить ее в VSPackage и затем запрограммировать его, чтобы быть активными или неактивными, чтобы управлять видимостью ваших команд:

1. Зарегистрируйте идентификаторы GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод.

2. Получить состояние идентификатор GUID контекста, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод.

3. Включать идентификаторы GUID контекста и отключать путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод.

> [!CAUTION]
> Убедитесь, что VSPackage не влияет на любого существующего контекста идентификаторы GUID, так как других пакетов VSPackage может зависеть от них.

## <a name="see-also"></a>См. также

- [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)
- [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)