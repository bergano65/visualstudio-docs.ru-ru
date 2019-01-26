---
title: Как выполнить Отправка сообщения электронной почты
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51546047a12e23c688ccfdfd05aeaa9c2ab89f95
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866731"
---
# <a name="how-to-programmatically-send-email"></a>Как выполнить Отправка сообщения электронной почты  
  Этот пример отправляет сообщение электронной почты, контакты, которые содержат имя домена **example.com** вводят адреса электронной почты.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Контакты, которые содержат имя домена **example.com** вводят адреса электронной почты.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Не удаляйте код фильтра, который ищет имя домена **example.com**. Решение будет отправлять сообщения электронной почты для всех контактов, если удалить фильтр.  
  
## <a name="see-also"></a>См. также  
 [Работа с элементами почты](../vsto/working-with-mail-items.md)   
 [Практическое руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Практическое руководство. Программный доступ к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
