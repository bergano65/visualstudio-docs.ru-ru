---
title: Цифры Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711858"
---
# <a name="enumerators"></a>Enumerators
В этом разделе перечислены типы данных регистратора в API-разъеме управления исходным управлением, о которым должен знать плагин управления исходным элементом.

## <a name="in-this-section"></a>В этом разделе
- [Командный код](../extensibility/command-code-enumerator.md) Перечисляет варианты для функций [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Сообщение](../extensibility/message-enumerator.md) Перечисляет флаги, используемые для обратного вызова печати, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Код статуса файла](../extensibility/file-status-code-enumerator.md) Содержит именованные постоянные значения, которые определяют состояние файла под контролем источника.

- [Код состояния каталога](../extensibility/directory-status-code-enumerator.md) Содержит именованные постоянные значения, которые определяют состояние каталога под контролем источника.

## <a name="related-sections"></a>См. также
- [Создание плагина управления исходным элементом](../extensibility/internals/creating-a-source-control-plug-in.md) Определяет подключаемый SDK управления исходным элементом и описывает включенные ресурсы.

- [SccgetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Подталкивает пользователя к расширенным опциям для данной команды.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Изучит список файлов для их текущего состояния. Кроме того, `pfnPopulate` использует функцию для уведомления вызываемого, когда `nCommand`файл не соответствует критериям для .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Описывает функцию обратного вызова, которая используется [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений от плагина управления исходным кодом через IDE.

- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md) Предоставляет полный список всех элементов в API для управления исходным управлением.
