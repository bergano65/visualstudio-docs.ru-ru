---
title: Отправка событий | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65c86cb8028d5c310de6f48c753d862865ea7a46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570808"
---
# <a name="sending-events"></a>Отправка событий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отправки событий](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-events).  
  
Механизм для обмена данными между отладчиком и модуль отладки (DE) — это модель событий, в зависимости от DCOM. События отправляются в виде COM-объектов, и каждое событие имеет параметры, которые определяют следующее:  
  
-   DE, который вызвал событие.  
  
-   Описание того, что произошло.  
  
-   Процесс, программу и сведения о потоке, определяющий контексте которой произошло событие. Процесс не отправляется для события, отправляемые с Развернутой.  
  
-   Тип события, который указывает, является ли событие синхронным или асинхронным.  
  
 Все события отладки отправляются с помощью метода [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Описание двух источников событий: модуль отладки (DE) и сеанс отладки manager (SDM).  
  
 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md)  
 Описание типов событий, поддерживаемые в настоящее время: асинхронные и синхронные.  
  
 [Описания событий](../../extensibility/debugger/event-descriptions.md)  
 Определяет события и причины их использования.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Описание работы Развернутой с помощью интерпретатора или операционной системы, для предоставления служб отладки.

