---
title: Отправка событий | Документация Майкрософт
description: Узнайте, как отладчик и модуль отладки используют модель событий на основе DCOM. События отправляются в виде COM-объектов.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0262868ae442bfdd8b99c16f59e000f4ebfc35c5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847914"
---
# <a name="send-events"></a>Отправка событий
Механизм обмена данными между отладчиком и модулем отладки (DE) — это модель событий, основанная на DCOM. События отправляются в виде COM-объектов, а каждое событие имеет параметры, которые указывают:

- Значение DE, которое вызвало событие.

- Описание того, что произошло.

- Сведения о процессе, программе и потоке, определяющие контекст, в котором произошло событие. Процесс не отправляется для событий, отправленных из DE.

- Тип события, указывающий, является ли событие синхронным или асинхронным.

  Все события отладки отправляются с помощью метода [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Содержание раздела
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Описание двух источников событий: Подсистема отладки (DE) и диспетчер отладки сеансов (SDM).

 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md) Обсуждаются типы событий, поддерживаемые в настоящее время: асинхронные и синхронные.

 [Описания событий](../../extensibility/debugger/event-descriptions.md) Определяет события и причины их использования.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Описывает, как DE работает с интерпретатором или операционной системой для предоставления служб отладки.
