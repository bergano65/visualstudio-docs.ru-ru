---
title: Как выполнить Программный доступ к контактам Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 662190d3db9c3d384d60f4953ea3809cb726f76c
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801727"
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
  
  