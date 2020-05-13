---
title: Отправка событий Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713033"
---
# <a name="send-events"></a>Отправка событий
Механизм связи между отладчиком и отладчиком (DE) представляет собой модель событий, основанную на DCOM. События отправляются как объекты COM, и каждое событие имеет параметры, которые указывают:

- DE, который назвал событие.

- Описание того, что произошло.

- Информация о процессе, программе и потоке, которая определяет контекст того, где произошло событие. Процесс не отправляется на события, отправленные из DE.

- Тип события, указывающий, является ли событие синхронным или асинхронным.

  Все события отладки отправляются методом [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>В этом разделе
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Объясняет два источника событий: движок отладки (DE) и диспетчер сеанса отладки (SDM).

 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md) Обсуждается поддерживаемые в настоящее время типы событий: асинхронные и синхронные.

 [Описания событий](../../extensibility/debugger/event-descriptions.md) Определяет события и причины их использования.

## <a name="related-sections"></a>См. также
 [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Описывает, как DE работает с переводчиком или операционной системой для предоставления услуг отладки.
