---
title: Интерфейс IDebugAsyncOperation | Документация Майкрософт
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
ms.openlocfilehash: c0088fddd2661d6711c9a18495f4b8704f782b3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349999"
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