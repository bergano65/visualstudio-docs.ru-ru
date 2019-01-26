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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f095d72e3e008da734eb60c2193a3003624e51a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966482"
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