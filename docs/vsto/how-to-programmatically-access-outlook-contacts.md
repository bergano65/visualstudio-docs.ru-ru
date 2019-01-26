---
title: Как выполнить Программный доступ к контактам Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b47d90eef38c5aff055b7ba2a05e39f8de17269
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873669"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Как выполнить Программный доступ к контактам Outlook
  Этот пример находит все контакты, фамилии которых содержат строку поиска.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, фамилии которых содержат строку "**н/д»** (например, Tzipi Butnaru) в **контакты** папки.  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами контактов](../vsto/working-with-contact-items.md)   
 [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Практическое руководство. Программный поиск адреса электронной почты в контактах](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Практическое руководство. Программное удаление контактов Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
