---
title: Программное выполнение действий при получении сообщения электронной почты
description: Сведения об использовании Visual Studio для программного выполнения настраиваемых действий при получении сообщения электронной почты в Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], actions when e-mail is received
- NewMail event
- mail items [Office development in Visual Studio], custom actions
- e-mail [Office development in Visual Studio], custom actions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 22dbd3ae72ac8c269de603ce22bbfebef669be08
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523885"
---
# <a name="how-to-programmatically-perform-actions-when-an-email-message-is-received"></a>Руководство. программное выполнение действий при получении сообщения электронной почты
  В этом примере выполняются пользовательские действия, когда пользователь получает сообщение электронной почты.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-vb[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_PerformActions/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_PerformActions#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_PerformActions/thisaddin.cs#1)]

## <a name="see-also"></a>См. также раздел
- [Как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
