---
title: Практическое руководство. Программное перемещение элементов в Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3dcbfbe7b6e6ac5bacb9e8e36e43d780d3051903
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812572"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Практическое руководство. Программное перемещение элементов в Outlook
  В этом примере перемещает непрочитанные сообщения электронной почты из **папки "Входящие"** в папку с именем **теста**. В примере перемещается только сообщения, которые содержат слово **теста** в `Subject` поля.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Папка почты Outlook с именем **теста**.

- Сообщение электронной почты с слово **теста** в `Subject` поля.

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Практическое руководство. Программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
