---
title: "Практическое руководство. Программный поиск в указанной папке"
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
  - "Outlook - папки [разработка решений Office в Visual Studio], поиск"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Практическое руководство. Программный поиск в указанной папке
  Данный пример кода использует методы `Find` и `FindNext` для поиска текста в поле темы сообщений электронной почты, содержащихся в папке **Входящие**.  Этот метод использует фильтр строк для поиска буквы "Т", обозначающей начальную букву текста `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  