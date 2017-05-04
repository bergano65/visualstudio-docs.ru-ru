---
title: "Практическое руководство. Программное определение текущего элемента Outlook | Microsoft Docs"
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
  - "электронная почта [разработка решений Office в Visual Studio], текущий элемент"
  - "элементы почты [разработка решений Office в Visual Studio], текущий"
  - "Outlook [разработка решений Office в Visual Studio], текущий элемент"
  - "SelectionChange - событие"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Практическое руководство. Программное определение текущего элемента Outlook
  В данном примере с помощью события Explorer.SelectionChange отображается имя текущей папки и некоторая информация о выбранном элементе.  Затем с помощью кода отображается выбранный элемент.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## Компиляция кода  
 Для этого примера необходимо следующее.  
  
-   Элементы встреч, контактов и электронной почты в Microsoft Office Outlook.  
  
## См. также  
 [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  