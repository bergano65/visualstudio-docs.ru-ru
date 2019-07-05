---
title: Найти адрес электронной почты в контактах программным способом
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26e32314db68ae064edac5537222447625cb051d
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328973"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Практическое руководство. Программный поиск адреса электронной почты в контактах
  В этом примере в папке контактов осуществляется поиск контактов, в адресах электронной почты которых содержится доменное имя **example.com** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Контакты, в адресах электронной почты которых содержится доменное имя **example.com** (например, `somebody@example.com`), а также имеющие имена и фамилии.

## <a name="see-also"></a>См. также
- [Работа с элементами контактов](../vsto/working-with-contact-items.md)
- [Практическое руководство. Отправка сообщения электронной почты](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Практическое руководство. Программный доступ к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Практическое руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
