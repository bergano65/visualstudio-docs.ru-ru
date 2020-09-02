---
title: Метод Нотифидебугжерофваиткомплетион | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153731"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод NotifyDebuggerOfWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Метод-заполнитель, используемый отладчиком в качестве цели точки останова. Этот метод не должен быть встроенным или оптимизированным.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Remarks  
 Все операции JOIN с задачей должны вызывать этот метод, если задан бит уведомления отладчика.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также:  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
