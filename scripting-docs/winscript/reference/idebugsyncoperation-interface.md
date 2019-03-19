---
title: Интерфейс IDebugSyncOperation | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7184be62a8ad2b65e81d1ad82f01f0ce3f4668c5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146387"
---
# <a name="idebugsyncoperation-interface"></a>Интерфейс IDebugSyncOperation
Позволяет модулю скриптов абстрагировать операцию (например, вычисление выражений), которую требуется выполнить вложенной в определенный заблокированный поток. Интерфейс также предоставляет механизм для отмены операций не отвечает.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSyncOperation` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Возвращает анализируемый поток приложения для данной синхронной операции.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Синхронно выполняет операцию и возвращает.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Отмена выполняемой операции в другом потоке.|