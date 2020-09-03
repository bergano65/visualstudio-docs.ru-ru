---
title: Отправка событий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713033"
---
# <a name="send-events"></a>Отправка событий
Механизм обмена данными между отладчиком и модулем отладки (DE) — это модель событий, основанная на DCOM. События отправляются в виде COM-объектов, а каждое событие имеет параметры, которые указывают:

- Значение DE, которое вызвало событие.

- Описание того, что произошло.

- Сведения о процессе, программе и потоке, определяющие контекст, в котором произошло событие. Процесс не отправляется для событий, отправленных из DE.

- Тип события, указывающий, является ли событие синхронным или асинхронным.

  Все события отладки отправляются с помощью метода [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>В этом разделе
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Описание двух источников событий: Подсистема отладки (DE) и диспетчер отладки сеансов (SDM).

 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md) Обсуждаются типы событий, поддерживаемые в настоящее время: асинхронные и синхронные.

 [Описания событий](../../extensibility/debugger/event-descriptions.md) Определяет события и причины их использования.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Описывает, как DE работает с интерпретатором или операционной системой для предоставления служб отладки.
