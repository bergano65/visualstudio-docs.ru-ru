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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5842b79e6dd38ed99a7a255b4164762b1dd1b68b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867353"
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
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)