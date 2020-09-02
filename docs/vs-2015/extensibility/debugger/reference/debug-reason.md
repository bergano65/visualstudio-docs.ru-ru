---
title: DEBUG_REASON | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95a537c703d4afd68bb291205e0c7da8d9b8fc59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143016"
---
# <a name="debug_reason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, почему процесс был запущен для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Произошла неспецифическая ошибка (используется в качестве условия по умолчанию, если по каким-либо причинам не подходит).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Процесс был запущен по запросу пользователя.  
  
 DEBUG_REASON_USER_ATTACHED  
 Этот уже запущенный процесс был подключен пользователем.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Процесс был автоматически присоединен к моменту запуска.  
  
 DEBUG_REASON_CAUSALITY  
 Процесс был запущен из-за JIT *-события* отладки.  
  
## <a name="remarks"></a>Remarks  
 Возвращается методом [жетдебугреасон](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
