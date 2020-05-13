---
title: Командный дизайн (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709663"
---
# <a name="command-design"></a>Командный дизайн
При добавлении команды в VSPackage необходимо указать, где она должна появиться, когда она доступна и как она должна быть обработана.

## <a name="define-commands"></a>Определение команд
 Чтобы определить новые команды, включите таблицу командVisual Studio *(.vsct)* в проект VSPackage. Если вы создали VSPackage с помощью шаблона пакета Visual Studio, проект включает в себя один из этих файлов. Для получения дополнительной информации смотрите [файлы командной таблицы Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio объединяет все файлы *.vsct,* которые она находит, чтобы отображать команды. Поскольку эти файлы отличаются от двоичных VSPackage, Visual Studio не нужно загружать пакет, чтобы найти команды. Для получения дополнительной информации см., [как VSPackages добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> использует атрибут регистрации для определения ресурсов меню и команд. Для получения дополнительной [Command implementation](../../extensibility/internals/command-implementation.md)информации см.

 Команды могут быть изменены во время выполнения несколькими различными способами. Они могут отображаться или скрыты, включены или отключены. Они могут отображать различные тексты или значки, или содержать различные значения. Большая настройка может быть выполнена до того, как Visual Studio загрузит ваш VSPackage. Для получения дополнительной информации см., [как VSPackages добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Обработчики команд
 При создании команды необходимо предоставить обработчик событий для выполнения команды. Если пользователь выбирает команду, она должна быть соответствующим образом направлена. Направление команды означает отправку в правильный VSPackage, чтобы включить или отключить ее, скрыть или отобразить, и выполнить его, если пользователь решит это сделать. Для получения дополнительной [Command routing algorithm](../../extensibility/internals/command-routing-algorithm.md)информации см.

## <a name="visual-studio-command-environment"></a>Среда команды Visual Studio
 Visual Studio может принимать любое количество VSPackages, и каждый может внести свой собственный набор команд. Среда отображает только команды, соответствующие текущей задаче. Для получения дополнительной [информации](../../extensibility/internals/command-availability.md) [Selection context objects](../../extensibility/internals/selection-context-objects.md)см.

 VSPackage, определяющий новые команды, меню, панели инструментов или меню ярлыков, предоставляет свою командную информацию Visual Studio во время установки через записи реестра, которые ссылаются на ресурсы в родных или управляемых сборках. Затем каждый ресурс ссылается на двоичный ресурс данных *(.cto)* файл, который производится при компиляции таблицы команд Visual Studio (*.vsct)* файл. Это позволяет Visual Studio предоставлять объединенные наборы команд, меню и панели инструментов без необходимости загружать каждый установленный VSPackage.

### <a name="command-organization"></a>Командная организация
 Среда позиционирует команды по группам, приоритету и меню.

- Группы представляют собой логические коллекции связанных команд, например, группы команд **Cut,** **Copy**и **Paste.** Группы - это команды, которые отображаются в меню.

- Приоритет определяет порядок отображаются в меню отдельными командами в группе.

- Меню выступает в качестве контейнеров для групп.

  Среда предварительно определяет некоторые команды, группы и меню. Для получения дополнительной [Default command, group, and toolbar placement](../../extensibility/internals/default-command-group-and-toolbar-placement.md)информации см.

  Команда может быть назначена основной группе. Основная группа контролирует положение команды в основной структуре меню и в поле **настраиваемых** диалогов. Команда может отображаться в нескольких группах; например, команда может быть в основном меню, в меню ярлыка и на панели инструментов. Для получения дополнительной информации см., [как VSPackages добавить элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Маршрутизация команд
 Процесс вызова и перехивания команд для VSPackages отличается от процесса вызова методов на объектных экземплярах.

 Маршруты среды последовательно выключают внутренний (локальный) контекст команды, основанный на текущем выборе, к внешнему (глобальному) контексту. Первый контекст, который способен выполнить команду, — это контекст, который ее обрабатывает. Для получения дополнительной [Command routing algorithm](../../extensibility/internals/command-routing-algorithm.md)информации см.

 В большинстве случаев среда обрабатывает команды <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> с помощью интерфейса. Поскольку схема командной схемы управления позволяет нескольким <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> различным объектам обрабатывать команды, может быть реализована любым количеством объектов; к ним относятся элементы управления Microsoft ActiveX, реализации представления окон, объекты документов, иерархии проектов и сами объекты VSPackage (для глобальных команд). В некоторых специализированных случаях, например, команды по <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> реучации в иерархии, интерфейс должен быть реализован.

## <a name="related-topics"></a>Связанные разделы

|Заголовок|Описание|
|-----------|-----------------|
|[Реализация командования](../../extensibility/internals/command-implementation.md)|Описывает, как реализовать команды в VSPackage.|
|[Доступность команд](../../extensibility/internals/command-availability.md)|Описывает, как контекст Visual Studio определяет, какие команды доступны.|
|[Алгоритм командной разработки](../../extensibility/internals/command-routing-algorithm.md)|Описывает, как архитектура командных реукторов Visual Studio позволяет обрабатывать команды различными VSPackages.|
|[Руководящие принципы размещения командования](../../extensibility/internals/command-placement-guidelines.md)|Предлагает, как позиционировать команды в среде Visual Studio.|
|[Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Описывает, как VSPackages лучше всего использовать архитектуру команды Visual Studio.|
|[Размещение команд, групп и панели инструментов по умолчанию](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Описывает, как VSPackages лучше всего использовать команды, которые включены в Visual Studio.|
|[Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)|Описывает, как Visual Studio загружает VSPackages.|
|[Таблица команд Visual Studio (.vsct) файлов](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Предоставляет информацию о *файлах .vsct* на основе XML, которые используются для описания макета и внешнего вида команд в VSPackages.|
