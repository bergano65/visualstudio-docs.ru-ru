---
title: Поиск адреса электронной почты в контактах программным способом
description: Узнайте, как можно использовать Visual Studio для программного поиска адреса электронной почты в контактах Microsoft Outlook.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7fa6578612fb81d9d025e613697c4342bac11bee
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528223"
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
