---
title: Практическое руководство. Программное сохранение вложений из элементов электронной почты Outlook
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 874f19e0ae4e752a36ce95deab669ab46bfbf038
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419525"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Практическое руководство. Программное сохранение вложений из элементов электронной почты Outlook
  В данном примере вложения электронной почты сохраняются в указанную папку, если почта поступает в папки "Входящие".

> [!IMPORTANT]
> Этот пример работает только в том случае, если вы добавите папку с именем **TestFileSave** в корневом каталоге.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>См. также
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Практическое руководство. Программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
