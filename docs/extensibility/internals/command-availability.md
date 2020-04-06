---
title: Доступность командования Документы Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709701"
---
# <a name="command-availability"></a>Доступность команд

Контекст Visual Studio определяет, какие команды доступны. Контекст может меняться в зависимости от текущего проекта, текущего редактора, загруженных VSPackages и других аспектов интегрированной среды разработки (IDE).

## <a name="command-contexts"></a>Контексты командования

Следующие контексты команд являются наиболее распространенными:

- IDE: Команды, предоставляемые IDE, всегда доступны.

- VSPackage: VSPackages может определить, когда команды должны отображаться или скрыты.

- Проект: Команды проекта отображаются только для выбранного в настоящее время проекта.

- Редактор: Только один редактор может быть активен одновременно. Команды от активного редактора доступны. Редактор работает в тесном контакте с языковой службой. Языковая служба должна обрабатывать свои команды в контексте связанного редактора.

- Тип файла: редактор может загрузить более одного типа файла. Доступные команды могут изменяться в зависимости от типа файла.

- Активное окно: Последнее активное окно документа устанавливает контекст пользовательского интерфейса (UI) для ключевых привязок. Однако окно инструментов, имеющее таблицу связывания ключей, напоминающую внутренний веб-браузер, также может установить контекст uI. Для многоэлементных окон документов, таких как HTML-редактор, каждая вкладка имеет другой контекст команды GUID. После регистрации окна инструмента он всегда доступен в меню **View.**

- Контекст uI: контексты uI определяются значениями <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> класса, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> например, когда строится <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> решение или когда отладчик активен. Несколько контекстов uI могут быть активны одновременно.

## <a name="define-custom-context-guids"></a>Определите пользовательские GUID-интерфейсы контекста

Если уже определен соответствующий контекст команды GUID, можно определить его в VSPackage, а затем запрограммировать его на активную или неактивную видимость команд:

1. Зарегистрируйте контекстНЫЕ GUID, позвонив по методу. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>

2. Получите состояние графического интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> контекста, позвонив по методу.

3. Включите и выключите и <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> выключите интерфейс контекста, вызывая метод.

> [!CAUTION]
> Убедитесь, что ваш VSPackage не влияет на любой существующий контекст GUIDs, потому что другие VSPackages может зависеть от них.

## <a name="see-also"></a>См. также

- [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)
- [Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
