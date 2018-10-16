---
title: Интерфейс IDebugThreadCall | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726944"
---
# <a name="idebugthreadcall-interface"></a>Интерфейс IDebugThreadCall
`IDebugThreadCall` Интерфейс обычно реализуется компонентом, который выполняет вызовы между потоками с `IDebugThread` маршалинг реализацию, предоставляемую диспетчером процесса отладки (PDM).  
  
 Вызовы PDM `IDebugThreadCall` интерфейса в нужный поток и `IDebugThreadCall` интерфейс отправляет вызов необходимого внедрения. `IDebugThreadCall` Интерфейс приводит сведения о параметрах, соответствующее верхней, передаваемый в параметрах.  
  
 `IDebugThreadCall` Интерфейс представляет собой объект свободных потоков.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugThreadCall` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Обрабатывает вызовы для выполнения кода в другом потоке.|