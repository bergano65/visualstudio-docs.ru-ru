---
title: Интерфейс IDebugAsyncOperation | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726104"
---
# <a name="idebugasyncoperation-interface"></a>Интерфейс IDebugAsyncOperation
Диспетчер отладки процессов реализует `IDebugAsyncOperation` интерфейса. Вызывает обработчик языка `IDebugApplication::CreateAsyncDebugOperation` метод для получения ссылки на этот интерфейс. Можно использовать обработчик языка `IDebugAsyncOperation` интерфейс для предоставления асинхронного доступа к операции синхронной отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugAsyncOperation` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Возвращает операцию синхронной отладки, связанные с этим объектом.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Вызывает асинхронную операцию начать.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Отменяет операцию.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Определяет, если завершения отладки.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Предоставляет параметр возвращаемого объекта из отладки синхронной операции и возвращаемое значение.|