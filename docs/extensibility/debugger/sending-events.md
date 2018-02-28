---
title: "Отправка событий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2bfdefc3202a026516edb3f9221e0626e1a83b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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