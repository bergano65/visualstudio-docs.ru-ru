---
title: Руководство. Программное перемещение элементов в Outlook
description: Сведения о программном перемещении элементов в Microsoft Outlook. В этом примере из папки "Входящие" перемещаются непрочитанные сообщения электронной почты в папку с именем Test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 770f056dc681e1ee2cd6704f9bd1d42afae4957b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888866"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Руководство. Программное перемещение элементов в Outlook
  В этом примере из папки **"Входящие"** перемещаются непрочитанные сообщения электронной почты в папку с именем **Test**. В этом примере в поле перемещаются только те сообщения, которые содержат слово **Test** `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Папка почты Outlook с именем **Test**.

- Сообщение электронной почты, поступающие по слову **Test** в `Subject` поле.

## <a name="see-also"></a>См. также раздел
- [Работа с папками](../vsto/working-with-folders.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программный поиск в определенной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Руководство. программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
