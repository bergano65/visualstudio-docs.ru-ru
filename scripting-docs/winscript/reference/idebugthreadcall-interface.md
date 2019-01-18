---
title: Интерфейс IDebugThreadCall | Документация Майкрософт
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
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346271"
---
# <a name="idebugthreadcall-interface"></a>Интерфейс IDebugThreadCall
`IDebugThreadCall` Интерфейс обычно реализуется компонентом, который выполняет вызовы между потоками с `IDebugThread` маршалинга предоставляет диспетчер отладки процессов (PDM).  
  
 Вызовы PDM `IDebugThreadCall` интерфейс в нужный поток и `IDebugThreadCall` интерфейс перенаправляет вызов необходимого внедрения. `IDebugThreadCall` Интерфейс приводит сведения о параметрах, переданной в параметрах соответствующего наверх.  
  
 `IDebugThreadCall` Интерфейс представляет собой свободнопоточный объект.  
  
## <a name="methods"></a>Методы  
 Помимо методов, наследуемых от `IUnknown`, `IDebugThreadCall` интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Обрабатывает вызовы для выполнения кода в другом потоке.|