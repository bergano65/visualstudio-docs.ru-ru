---
title: IDebugProcess2::GetAttachedSessionName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4607026040bb790e34bf39fcd2b9cdf911251c81
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962825"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Получает имя сеанса, который выполняет отладку этого процесса. Интегрированная среда разработки для отображения этой информации для пользователя, который выполняет отладку определенного процесса на конкретном компьютере.  
  
> [!NOTE]
>  Этот метод является устаревшим, и ее реализация должна всегда возвращать `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод должен всегда возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)