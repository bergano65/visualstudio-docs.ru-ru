---
title: 'Практическое: программное определение текущего элемента Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 519fd1572b3ebb1faf8cc7adc6d5a9ba2773d67b
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257054"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Практическое: программное определение текущего элемента Outlook
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
 [Практическое: программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое: программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  