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
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>Отправка событий
Механизм обмена данными между отладчиком и ядро отладки (DE) это событие модель, основанная на DCOM. События отправляются в виде объектов COM, и каждое событие имеет параметры, которые определяют следующее:  
  
-   DE, который вызвал событие.  
  
-   Описание того, что произошло.  
  
-   Процесс, программы и сведения о потоке, определяющий контексте которой произошло событие. Процесс не отправляется для события, отправляемые с DE.  
  
-   Тип события, которое указывает, является ли событие синхронным или асинхронным.  
  
 Все события отладки отправляются с помощью метода [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Содержание  
 [Источники событий](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Описание двух источников событий: ядро отладки (DE) и сеанс отладки manager (SDM).  
  
 [Поддерживаемые типы событий](../../extensibility/debugger/supported-event-types.md)  
 Описывает типы событий в настоящее время поддерживаются: асинхронном и синхронном способе.  
  
 [Описания событий](../../extensibility/debugger/event-descriptions.md)  
 Определяет события и причины их использования.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Описывает работу DE интерпретатор или операционной системы, для предоставления служб отладки.
