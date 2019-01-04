---
title: Как выполнить Программное определение текущего элемента Outlook
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 93d1d565664e9851310e9138fef7f6d14041c865
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945955"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Как выполнить Программное определение текущего элемента Outlook
  В этом примере используется `Explorer.SelectionChange` событий, чтобы отобразить имя текущей папки и некоторые сведения о выбранном элементе. Затем код отображает выбранный элемент.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Встречи, контакты и сообщения электронной почты в Microsoft Office Outlook.  
  
## <a name="see-also"></a>См. также  
 [Обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
