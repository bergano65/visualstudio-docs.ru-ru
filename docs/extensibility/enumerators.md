---
title: Перечислители | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711858"
---
# <a name="enumerators"></a>Enumerators
В этом разделе перечислены типы данных перечислителя в интерфейсе API подключаемого модуля системы управления версиями, о которых должен быть знаком подключаемый модуль системы управления версиями.

## <a name="in-this-section"></a>В этом разделе
- [Код команды](../extensibility/command-code-enumerator.md) Перечисляет параметры для функций [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [сккпопулателист](../extensibility/sccpopulatelist-function.md) .

- [Сообщение об ошибке](../extensibility/message-enumerator.md) Перечисляет флаги, используемые для обратного вызова печати, [лптекстаутпрок](../extensibility/lptextoutproc.md).

- [Код состояния файла](../extensibility/file-status-code-enumerator.md) Содержит именованные постоянные значения, которые определяют состояние файла в системе управления версиями.

- [Код состояния каталога](../extensibility/directory-status-code-enumerator.md) Содержит именованные постоянные значения, которые определяют состояние каталога в системе управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md) Определяет пакет SDK для подключаемого модуля системы управления версиями и описывает входящие ресурсы.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Запрашивает у пользователя дополнительные параметры для данной команды.

- [Сккпопулателист](../extensibility/sccpopulatelist-function.md) Проверяет список файлов на предмет их текущего состояния. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand` .

- [Лптекстаутпрок](../extensibility/lptextoutproc.md) Описывает функцию обратного вызова, используемую [сккопенпрожект](../extensibility/sccopenproject-function.md) для вывода сообщений из подключаемого модуля системы управления версиями через интегрированную среду разработки.

- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md) Содержит полный список всех элементов в интерфейсе API подключаемого модуля системы управления версиями.
