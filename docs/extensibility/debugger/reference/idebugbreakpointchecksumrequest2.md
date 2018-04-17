---
title: IDebugBreakpointChecksumRequest2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb319b14e1d373abe3c0634c768bfe1dcb04f539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Представляет документ контрольной суммы для запроса точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализованный [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладки пакета и используемые отладчики.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugBreakpointChecksumRequest2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Возвращает контрольную сумму документа для запроса останова Получает уникальный идентификатор алгоритма подсчета контрольной суммы для использования.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Определяет, включена ли контрольная сумма для этого документа.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll