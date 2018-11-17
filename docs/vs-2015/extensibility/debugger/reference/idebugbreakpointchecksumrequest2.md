---
title: IDebugBreakpointChecksumRequest2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0cb4c9de41f53c2bcbf7cc329f5537c2633aa6f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765452"
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
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Извлекает контрольная сумма документа для запроса точки останова Получает уникальный идентификатор алгоритма подсчета контрольной суммы для использования.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Определяет, включена ли контрольная сумма для этого документа.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

