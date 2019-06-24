---
title: Программным способом получить непрочитанных сообщений из папки "Входящие"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9a718d6a8ee4eb633b34e1e12f85d578dc99fa6
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328932"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Практическое руководство. Программное извлечение непрочитанных сообщений из папки "Входящие"
  В этом примере извлекаются непрочитанные электронные письма из Outlook **папки "Входящие"** и отображает число элементов.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>См. также
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Практическое руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Практическое руководство. Отправка сообщения электронной почты](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
