---
title: DEBUG_REASON | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 883630e7c9e00a58eac143a6cde7ee40109bb4e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573380"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DEBUG_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reason).  
  
Указывает, почему был запущен процесс для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
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

