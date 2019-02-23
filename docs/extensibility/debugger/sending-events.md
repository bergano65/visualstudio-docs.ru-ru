---
title: Отправка событий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd282dd38d322a5b7d9821406d30a303fabb02bb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685070"
---
# <a name="send-events"></a>Отправка событий
Механизм для обмена данными между отладчиком и модуль отладки (DE) — это модель событий, в зависимости от DCOM. События отправляются в виде COM-объектов, и каждое событие имеет параметры, задающие:

- DE, который вызвал событие.

- Описание того, что произошло.

- Процесс, программу и сведения о потоке, определяющий контексте которой произошло событие. Процесс не отправляется для события, отправляемые с Развернутой.

- Тип события, который указывает, является ли событие синхронным или асинхронным.

  Все события отладки отправляются с помощью метода [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Содержание раздела
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md) объясняет два источника событий: модуль отладки (DE) и сеанс отладки manager (SDM).

 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md) рассматриваются типы событий, поддерживаемые в настоящее время: асинхронные и синхронные.

 [Описания событий](../../extensibility/debugger/event-descriptions.md) определяет события и причины их использования.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) описывает работу Развернутой с интерпретатор или операционной системы, для предоставления служб отладки.