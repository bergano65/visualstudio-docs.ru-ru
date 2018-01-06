---
title: "Как: программный доступ к контактам Outlook | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: contacts [Office development in Visual Studio], searching
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44799a88e0c08999452e5425e3e7d175feb8ec56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Практическое руководство. Программное получение доступа к контактам Outlook
  Этот пример находит все контакты, фамилии которых содержат строку поиска.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, фамилии которых содержат строку «**н/д»** (например, Tzipi Butnaru) в **контактов** папки.  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами контактов](../vsto/working-with-contact-items.md)   
 [Как: программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Как: программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Как: программный поиск адреса электронной почты в контактах](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Практическое руководство. Программное удаление контактов Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  