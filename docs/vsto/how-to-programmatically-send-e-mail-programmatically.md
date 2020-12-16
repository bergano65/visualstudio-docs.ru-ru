---
title: Руководство. Программная отправка электронной почты
description: Использование Visual Studio для программной отправки сообщения электронной почты из Microsoft Outlook. В этом примере сообщение электронной почты отправляется контактам, имеющим имя домена example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: 5f31fdb92a5acff16b1d6e8001ea88931a9a22ab
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525370"
---
# <a name="how-to-programmatically-send-email"></a>Руководство. Программная отправка электронной почты
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

## <a name="see-also"></a>См. также раздел
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Руководство. программный доступ к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Руководство. программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
