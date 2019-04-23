---
title: Практическое руководство. Программное определение текущего элемента Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5566538b428502c8e63e752463b0271daeac2918
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052510"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Практическое руководство. Программное определение текущего элемента Outlook
  В этом примере используется `Explorer.SelectionChange` событий, чтобы отобразить имя текущей папки и некоторые сведения о выбранном элементе. Затем код отображает выбранный элемент.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Встречи, контакты и сообщения электронной почты в Microsoft Office Outlook.

## <a name="see-also"></a>См. также
- [Обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
