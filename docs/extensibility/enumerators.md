---
title: Перечислители | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37f469ecc0ae097592a128b30a6a6f189d58d94b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689750"
---
# <a name="enumerators"></a>Перечислители.
В этом разделе перечислены типы данных перечислителя в API подключаемого модуля управления источник, подключаемый модуль системы управления версиями необходимо знать.

## <a name="in-this-section"></a>Содержание раздела
- [Команда кода](../extensibility/command-code-enumerator.md) перечисляет параметры для [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md) функции.

- [Сообщение](../extensibility/message-enumerator.md) перечисляет флаги, используемые для печати обратного вызова, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Файл состояния код](../extensibility/file-status-code-enumerator.md) Contains, именованных констант, определяющих состояние файла в системе управления версиями.

- [Код состояния Directory](../extensibility/directory-status-code-enumerator.md) Contains, с именем константы, определяющие состояние каталога в системе управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md) SDK подключаемого модуля управления источника определяет и описывает включаемые ресурсы.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) запрашивает у пользователя Дополнительные параметры для данной команды.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) описывает функцию обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.

- [Подключаемые модули управления источника](../extensibility/source-control-plug-ins.md) полный список всех элементов в API подключаемых модулей управления источника.