---
title: Отправка событий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204741"
---
# <a name="sending-events"></a>Отправка событий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Механизм обмена данными между отладчиком и модулем отладки (DE) — это модель событий, основанная на DCOM. События отправляются в виде COM-объектов, а каждое событие имеет параметры, которые определяют следующее:  
  
- Значение DE, которое вызвало событие.  
  
- Описание того, что произошло.  
  
- Сведения о процессе, программе и потоке, определяющие контекст, в котором произошло событие. Процесс не отправляется для событий, отправленных из DE.  
  
- Тип события, указывающий, является ли событие синхронным или асинхронным.  
  
  Все события отладки отправляются с помощью метода [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Описание двух источников событий: Подсистема отладки (DE) и диспетчер отладки сеансов (SDM).  
  
 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md)  
 Обсуждаются типы событий, поддерживаемые в настоящее время: асинхронные и синхронные.  
  
 [Описания событий](../../extensibility/debugger/event-descriptions.md)  
 Определяет события и причины их использования.  
  
## <a name="related-sections"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Описывает, как DE работает с интерпретатором или операционной системой для предоставления служб отладки.
