---
title: Отправка событий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>Отправка событий
Механизм для обмена данными между отладчиком и модуль отладки (DE) это событие модель, основанная на DCOM. События отправляются в виде COM-объектов, и каждое событие имеет параметры, укажите следующее:  
  
-   DE, который вызвал событие.  
  
-   Описание того, что произошло.  
  
-   Процесс, программы и сведения о потоке, определяющий контексте которой произошло событие. Процесс не отправляется для события, отправляемые из DE.  
  
-   Тип события, который указывает, является ли событие синхронным или асинхронным.  
  
 Все события отладки отправляются с помощью метода [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Описание двух источников событий: модуль отладки (DE) и сеанс отладки manager (SDM).  
  
 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md)  
 Описывает типы событий, поддерживаемых в настоящее время: асинхронная и синхронная.  
  
 [Описания событий](../../extensibility/debugger/event-descriptions.md)  
 Определяет события и причины их использования.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Описание работы Развернутой с помощью интерпретатора или операционной системы, для предоставления служб отладки.