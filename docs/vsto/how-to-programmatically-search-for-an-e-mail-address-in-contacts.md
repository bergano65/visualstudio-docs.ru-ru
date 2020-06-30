---
title: Поиск адреса электронной почты в контактах программным способом
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: a4a9d52ae16b77b40461a314c6008f8cdd741bcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537648"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Руководство. Программный поиск адреса электронной почты в контактах
  В этом примере в папке контактов осуществляется поиск контактов, в адресах электронной почты которых содержится доменное имя **example.com** .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Контакты, в адресах электронной почты которых содержится доменное имя **example.com** (например, `somebody@example.com`), а также имеющие имена и фамилии.

## <a name="see-also"></a>См. также раздел
- [Работа с элементами контактов](../vsto/working-with-contact-items.md)
- [Руководство. Программная отправка электронной почты](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Руководство. программный доступ к контактам Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
