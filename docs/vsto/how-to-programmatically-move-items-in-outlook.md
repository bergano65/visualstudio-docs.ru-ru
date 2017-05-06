---
title: "Практическое руководство. Программное перемещение элементов в Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook - папки [разработка решений Office в Visual Studio], перемещение элементов"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Практическое руководство. Программное перемещение элементов в Outlook
  В данном примере непрочитанные сообщения электронной почты перемещаются из папки **Входящие** в папку **Тест**.  В этом примере перемещаются только те сообщения, у которых в поле `Subject` есть слово **Тест**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## Компиляция кода  
 Для этого примера необходимо следующее.  
  
-   Папка почты Outlook с именем **Тест**.  
  
-   Сообщение электронной почты, которое поступает со словом **Тест** в поле `Subject`.  
  
## См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  