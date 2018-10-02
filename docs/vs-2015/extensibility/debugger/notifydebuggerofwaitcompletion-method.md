---
title: Метод NotifyDebuggerOfWaitCompletion | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4429b89be624960b787b51c3fa085f43e412889e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560873"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод NotifyDebuggerOfWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [метод NotifyDebuggerOfWaitCompletion](https://docs.microsoft.com/visualstudio/extensibility/debugger/notifydebuggerofwaitcompletion-method).  
  
Метод заполнитель, используемый как целевой объект точки останова в отладчике. Этот метод не должен быть встроенным или оптимизированного.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Примечания  
 Этот метод следует вызывать все операции соединения с задачей, если их отладчик уведомлений бита.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)

