---
title: DEBUG_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6102c0897c80fc927713d2f8bb1e5c83708e6bd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000202"
---
# <a name="debugreason"></a>DEBUG_REASON
Указывает, почему был запущен процесс для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 DEBUG_REASON_ERROR  
 Произошла общая ошибка (используется как условие по умолчанию при ни с одним другим причинам, по размеру).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Процесс был запущен по запросу пользователя.  
  
 DEBUG_REASON_USER_ATTACHED  
 Уже выполняемым процессам был подключен к этим пользователем.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Процесс автоматически присоединяется к, если оно было запущено.  
  
 DEBUG_REASON_CAUSALITY  
 Процесс был запущен из-за *Just-In-Time* событие отладки (JIT).  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) метод.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)