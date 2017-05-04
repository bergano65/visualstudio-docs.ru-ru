---
title: "Практическое руководство. Программное получение доступа к контактам Outlook | Microsoft Docs"
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
  - "контакты [разработка решений Office в Visual Studio], поиск"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Практическое руководство. Программное получение доступа к контактам Outlook
  Этом пример находит все контакты, фамилии которых содержат указанную строку поиска.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## Компиляция кода  
 Для этого примера необходимо следующее.  
  
-   Контакты, фамилии которых содержат строку "**Na"** \(например, Tzipi Butnaru\) в папке **Контакты**.  
  
## См. также  
 [Работа с элементами контактов](../vsto/working-with-contact-items.md)   
 [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Практическое руководство. Программный поиск адреса электронной почты в контактах](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Практическое руководство. Программное удаление контактов Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  