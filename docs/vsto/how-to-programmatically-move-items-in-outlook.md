---
title: "Как: программное перемещение элементов в Outlook | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b77524d5f297ada0e4821e229d9bb981518f9730
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Практическое руководство. Программное перемещение элементов в Outlook
  В этом примере перемещает непрочитанные сообщения электронной почты из **папки "Входящие"** в папку с именем **теста**. В примере показано перемещение только сообщения, которые содержат слово **тест** в `Subject` поле.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Папка почты Outlook с именем **теста**.  
  
-   Сообщение электронной почты, которое поступает со словом **тест** в `Subject` поле.  
  
## <a name="see-also"></a>См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Как: программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Как: программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  