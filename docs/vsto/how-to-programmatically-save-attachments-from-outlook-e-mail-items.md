---
title: 'Практическое: программное сохранение вложений из элементов электронной почты Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd564b71622ad5f9ee6500ddc3864bad0b21686b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674454"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Практическое: программное сохранение вложений из элементов электронной почты Outlook
  В данном примере вложения электронной почты сохраняются в указанную папку, если почта поступает в папки "Входящие".  
  
> [!IMPORTANT]  
>  Этот пример работает только в том случае, если вы добавите папку с именем **TestFileSave** в корневом каталоге.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами почты](../vsto/working-with-mail-items.md)   
 [Практическое: программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое: программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Практическое: программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  