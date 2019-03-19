---
title: Интерфейс IDebugThreadCall | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149527"
---
# <a name="idebugthreadcall-interface"></a>Интерфейс IDebugThreadCall
`IDebugThreadCall` Интерфейс обычно реализуется компонентом, который выполняет вызовы между потоками с `IDebugThread` маршалинга предоставляет диспетчер отладки процессов (PDM).  
  
 Вызовы PDM `IDebugThreadCall` интерфейс в нужный поток и `IDebugThreadCall` интерфейс перенаправляет вызов необходимого внедрения. `IDebugThreadCall` Интерфейс приводит сведения о параметрах, переданной в параметрах соответствующего наверх.  
  
 `IDebugThreadCall` Интерфейс представляет собой свободнопоточный объект.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugThreadCall` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Обрабатывает вызовы для выполнения кода в другом потоке.|