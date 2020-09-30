---
title: Программное сохранение вложений из сообщений электронной почты Outlook
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
ms.openlocfilehash: 3ade05e936397f72a0b370cb69d8be3310c3aee8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584772"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Как программно сохранять вложения из сообщений электронной почты Outlook

В данном примере вложения электронной почты сохраняются в указанную папку, если почта поступает в папки "Входящие".

> [!IMPORTANT]
> Этот пример работает только при добавлении папки с именем **тестфилесаве** в корневую папку каталога C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>См. также

- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Руководство. Программный поиск в определенной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
