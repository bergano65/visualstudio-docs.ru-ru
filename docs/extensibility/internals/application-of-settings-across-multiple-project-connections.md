---
title: Применение настроек по нескольким соединениям проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710062"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Применение параметров в нескольких соединениях проекта
Плагин управления исходным кодом, встроенный с помощью Подключаемого варианта API 1.2, может использовать пакетную операцию для выполнения одной и той же операции управления исходным кодом в нескольких проектах или нескольких контекстах подключения. Пакеты могут быть использованы для устранения избыточных, для одного проекта диалоговых коробок из пользовательского опыта.

 Если пользователь выбирает несколько элементов, которые принадлежат к более чем одному соединению в плагине управления исходным элементом, построенном с помощью Подключаемого варианта API 1.1 управления исходного элемента (например, два веб-проекта на разных машинах обмена файлами) и проверяет их, пользователь видит один и тот же диалоговый ящик неоднократно. Этот сценарий возникает даже в том случае, если пользователь нажимает **на apply to All** check box в диалоговом поле, потому что IDE сбрасывает свое состояние для каждого контекста соединения.

## <a name="new-capability-flag"></a>Новый флаг возможностей
 `SccBeginBatch` Функция устанавливает `SCC_CAP_BATCH` флаг, чтобы указать, что выполняется пакетная операция.

## <a name="new-functions"></a>Новые функции
Следующие новые функции поддерживают пакетную операцию:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Функция `SCCBeginBatch` запускает группу операций управления исходным источником. Функция `SccEndBatch` закрывает группу. Группы не могут быть вложены.

## <a name="see-also"></a>См. также
- [Что нового в версии API-элемента управления исходным элементом](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
