---
title: Практическое руководство. Отправка электронной почты программными средствами
ms.date: 08/14/2019
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
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551758"
---
# <a name="how-to-programmatically-send-email"></a>Практическое руководство. Отправка электронной почты программными средствами
  В этом примере в адреса электронной почты отправляются контакты с доменным именем **example.com** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Контакты, имеющие доменное имя **example.com** в своих адресах электронной почты.

## <a name="robust-programming"></a>Отказоустойчивость
 Не удаляйте код фильтра, который ищет доменное имя **example.com**. При удалении фильтра решение будет отправлять сообщения всем контактам по электронной почте.

## <a name="see-also"></a>См. также
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Практическое руководство. Создание элемента электронной почты программным способом](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Практическое руководство. Доступ к контактам Outlook программным способом](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
