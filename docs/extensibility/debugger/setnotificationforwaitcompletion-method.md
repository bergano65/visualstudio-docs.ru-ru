---
title: "Метод SetNotificationForWaitCompletion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Метод SetNotificationForWaitCompletion, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Метод SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Устанавливает или снимает бит TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION состояния.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
## Синтаксис  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### Параметры  
 `enabled`  
  
 `true` Чтобы установить бит; `false` с незаданным бит.  
  
## Исключения  
  
## Заметки  
 Отладчик установит этот бит для пошагового из тела асинхронного метода. Если `enabled` является `true`, этот метод должен вызываться только на задачу, которая еще не завершена. Если `enabled` является `false`, этот метод может вызываться для завершенных задач. В любом случае он должен использоваться только для стиля обещание задачи.  
  
## Требования  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)