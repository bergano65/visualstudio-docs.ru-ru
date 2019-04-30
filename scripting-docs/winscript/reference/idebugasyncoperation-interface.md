---
title: Интерфейс IDebugAsyncOperation | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821787"
---
# <a name="idebugasyncoperation-interface"></a>Интерфейс IDebugAsyncOperation
Диспетчер отладки процессов реализует `IDebugAsyncOperation` интерфейс. Вызывает модуль языка `IDebugApplication::CreateAsyncDebugOperation` метод для получения ссылки на этот интерфейс. Можно использовать модуль языка `IDebugAsyncOperation` интерфейс, чтобы предоставить асинхронный доступ к синхронной операции отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugAsyncOperation` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Возвращает операцию синхронной отладки, связанного с данным объектом.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Вызывает асинхронную операцию, чтобы начать.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Отменяет операцию.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Определяет, ли завершена операция отладки.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Предоставляет возвращаемое значение и параметр возвращаемого объекта из синхронной операции отладки.|