---
title: IDebugBreakpointChecksumRequest2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d06656ba05c3356d9f2a148045adbf4538c5ae5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431619"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет контрольную сумму документа для запроса точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализованный [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пакет отладки и используемый отладчиков.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugBreakpointChecksumRequest2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Извлекает контрольная сумма документа для запроса точки останова Получает уникальный идентификатор алгоритма подсчета контрольной суммы для использования.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Определяет, включена ли контрольная сумма для этого документа.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
