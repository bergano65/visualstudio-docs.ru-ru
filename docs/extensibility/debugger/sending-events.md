---
title: Отправка событий | Документация Майкрософт
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
ms.openlocfilehash: 369a2aa92c47c4db7b1036097ffb49f6d8de8a14
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895422"
---
# <a name="send-events"></a>Отправка событий
Механизм для обмена данными между отладчиком и модуль отладки (DE) — это модель событий, в зависимости от DCOM. События отправляются в виде COM-объектов, и каждое событие имеет параметры, задающие:  
  
- DE, который вызвал событие.  
  
- Описание того, что произошло.  
  
- Процесс, программу и сведения о потоке, определяющий контексте которой произошло событие. Процесс не отправляется для события, отправляемые с Развернутой.  
  
- Тип события, который указывает, является ли событие синхронным или асинхронным.  
  
  Все события отладки отправляются с помощью метода [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Описание двух источников событий: модуль отладки (DE) и сеанс отладки manager (SDM).  
  
 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md)  
 Описание типов событий, поддерживаемые в настоящее время: асинхронные и синхронные.  
  
 [Описания событий](../../extensibility/debugger/event-descriptions.md)  
 Определяет события и причины их использования.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Описание работы Развернутой с помощью интерпретатора или операционной системы, для предоставления служб отладки.