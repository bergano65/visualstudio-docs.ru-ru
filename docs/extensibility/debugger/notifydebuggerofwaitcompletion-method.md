---
title: "Метод NotifyDebuggerOfWaitCompletion | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bfd605665627bcc9269f9225acb7d2e12418ab4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод NotifyDebuggerOfWaitCompletion
Метод заполнителя, используется как целевой объект точки останова в отладчике. Этот метод не должен быть встроенным или оптимизированного.  
  
 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Примечания  
 Этот метод следует вызывать все операции соединения с задачей при их отладчик уведомления бита.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Task-класс](../../extensibility/debugger/task-class-internal-members.md)