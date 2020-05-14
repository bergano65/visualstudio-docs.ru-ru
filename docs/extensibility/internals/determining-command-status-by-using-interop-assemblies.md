---
title: Определение командного статуса с помощью межопом ныхабаший (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708704"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Определение статуса команды с помощью межопомнейных сборок
VSPackage должен отслеживать состояние команд, с которыми он может обрабатывать. Среда не может определить, когда команда, обрабатываемый в вашем VSPackage, становится включенной или отключенной. Ваш VSPackage несет ответственность за информирование среды о состояниях команд, например, о состоянии общих команд, таких как **Cut,** **Copy**и **Paste.**

## <a name="status-notification-sources"></a>Источники уведомлений о статусе
 Среда получает информацию о командах с <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> помощью метода VSPackages, который <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> является частью реализации интерфейса VSPackage. Окружающая среда <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> называет метод VSPackage при двух условиях:

- Когда пользователь открывает основное меню или контекстное меню (по правому нажатию), среда выполняет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод во всех командах этого меню, чтобы определить их состояние.

- Когда VSPackage просит среду обновить текущий пользовательский интерфейс (UI). Это обновление происходит как команды, которые в настоящее время видны пользователю, такие как **Cut,** **Copy**и **Paste** группирования на стандартной панели инструментов, становятся включенными и отключены в ответ на контекст и действия пользователя.

  Поскольку оболочка содержит несколько VSPackages, производительность оболочки недопустимо ухудшится, если она будет требовать опроса каждого VSPackage для определения статуса команды. Вместо этого ваш VSPackage должен активно уведомлять окружающую среду при изменении его uI во время изменения. Для получения дополнительной информации об уведомлении об [обновлении см.](../../extensibility/updating-the-user-interface.md)

## <a name="status-notification-failure"></a>Сбой уведомления о состоянии
 Неспособность VSPackage уведомить среду об изменении состояния команды может привести к несогласованности uI. Помните, что любая из команд меню или контекстного меню может быть помещена пользователем на панель инструментов. Поэтому обновление uI только тогда, когда меню или контекстное меню открывается, недостаточно.

## <a name="see-also"></a>См. также
- [Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Реализация](../../extensibility/internals/command-implementation.md)
