---
title: "Практическое руководство. Программный поиск адреса электронной почты в контактах"
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
  - "электронная почта [разработка решений Office в Visual Studio], поиск"
  - "контакты [разработка решений Office в Visual Studio], поиск"
  - "поиск контактов"
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Практическое руководство. Программный поиск адреса электронной почты в контактах
  В этом примере в папке контактов осуществляется поиск контактов, в адресах электронной почты которых содержится доменное имя **example.com**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_SearchEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchEmail/CS/thisaddin.cs#1)]  
  
## Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, в адресах электронной почты которых содержится доменное имя **example.com** \(например, `somebody@example.com`\), а также имеющие имена и фамилии.  
  
## См. также  
 [Работа с элементами контактов](../vsto/working-with-contact-items.md)   
 [Практическое руководство. Отправка сообщений электронной почты программными средствами](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Практическое руководство. Программное получение доступа к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  