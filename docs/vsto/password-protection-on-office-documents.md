---
title: "Защита паролей в документах Office"
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
  - "документы [разработка решений Office в Visual Studio], ограниченные разрешения"
  - "Office - документы [разработка решений Office в Visual Studio], ограниченные разрешения"
  - "пароли [разработка решений Office в Visual Studio], защиты документов"
  - "разрешения [разработка решений Office в Visual Studio"
  - "книги [разработка решений Office в Visual Studio], ограниченные разрешения"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Защита паролей в документах Office
  Для документов Microsoft Office Word и книг Microsoft Office Excel может устанавливаться пароль, таким образом, содержащиеся в них данные не будут открыты для несанкционированного доступа.  Этот параметр называется **Пароль для открытия**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Проекты уровня документа можно создавать с помощью существующих документов и книг, для которых включена функция **Пароль для открытия**.  Поведение в Visual Studio отличается от поведения в документах Word и Excel, для которых активирована функция **Пароль для открытия**.  
  
 Инструкции по включению функции **Пароль для открытия** см. в разделе справки в Word или Excel.  
  
## Поведение Excel и Word  
 Каждый раз при открытии книги Excel, для которой включена функция **Пароль для открытия** в Visual Studio, Excel запрашивает пароль.  Во время построения решения также будет запрашиваться пароль, поскольку документ открыт в режиме построения.  
  
 При первом открытии документа Word, для которого включена функция **Пароль для открытия** в Visual Studio, Excel запрашивает пароль.  После указания пароля запрос **Пароль для открытия** удаляется из документа и последующие доступы к документу производятся без указания пароля.  Чтобы ограничить доступ к документу, следует активировать функцию **Пароль для открытия** после завершения последнего построения и перед развертыванием решения.  
  
## См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Общие сведения об управлении правами на доступ к данным и расширениях управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Практическое руководство. Выполнение с выделенным кодом документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  