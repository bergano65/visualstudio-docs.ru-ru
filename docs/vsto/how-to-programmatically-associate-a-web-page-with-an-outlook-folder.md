---
title: "Практическое руководство. Программное связывание веб-страницы с папкой Outlook"
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
  - "папки [разработка решений Office в Visual Studio], и веб-страницы"
  - "Outlook [разработка решений Office в Visual Studio], веб-страницы, присоединенные к папкам"
  - "веб-страницы [разработка решений Office в Visual Studio], папки Outlook"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Практическое руководство. Программное связывание веб-страницы с папкой Outlook
  В данном примере выполняется поиск папки с именем `HtmlView` в Microsoft Office Outlook.  Если такая папка не существует, то код создает ее и связывает с ней веб\-страницу.  Если папка существует, код отображает ее содержимое.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программное создание настраиваемых элементов папок](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  