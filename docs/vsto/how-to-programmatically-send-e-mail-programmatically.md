---
title: "Практическое руководство. Отправка сообщений электронной почты программными средствами | Microsoft Docs"
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
  - "электронная почта [разработка решений Office в Visual Studio], отправка"
  - "элементы почты [разработка решений Office в Visual Studio], отправка электронной почты"
  - "Outlook [разработка решений Office в Visual Studio], создание электронной почты"
  - "Outlook [разработка решений Office в Visual Studio], отправка электронной почты"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Практическое руководство. Отправка сообщений электронной почты программными средствами
  В этом примере выполняется отправка сообщений электронной почты контактам, в адресах которых содержится имя домена **example.com**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Пример  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## Компиляция кода  
 Для этого примера необходимо следующее.  
  
-   Контакты, в адресах которых содержится имя домена **example.com**.  
  
## Отказоустойчивость  
 Не удаляйте код фильтра, в котором осуществляется поиск по имени домена **example.com**.  Если удалить фильтр, будет выполнена отправка сообщений электронной почты всем контактам.  
  
## См. также  
 [Работа с элементами почты](../vsto/working-with-mail-items.md)   
 [Практическое руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Практическое руководство. Программное получение доступа к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  