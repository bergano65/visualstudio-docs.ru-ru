---
title: "Разрешение вопросов, связанных с исключениями: System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "StackOverflowException - класс"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.StackOverflowException
Исключение <xref:System.StackOverflowException> вызывается, когда стек выполнения переполнен слишком большим количеством вложенных вызовов метода.  
  
## Полезные советы  
 Убедитесь, что в программе нет бесконечного цикла или бесконечной рекурсии.  
 Слишком большое количество вызовов метода часто говорит об очень глубокой или неограниченной рекурсии.  
  
## Примечания  
 Нельзя перехватить исключение переполнения стека, поскольку код обработки исключения может требовать стек. Вместо этого при переполнении стека в обычных приложениях среда CLR завершает процесс.  
  
 Приложение, в котором находится среда CLR, может изменить поведение по умолчанию и указать, чтобы среда CLR выгружала домен приложения, в котором произошло исключение, но позволяла процессу продолжаться. Для получения дополнительной информации см. [Интерфейс ICLRPolicyManager](../Topic/ICLRPolicyManager%20Interface.md).  
  
## См. также  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Циклические структуры](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)