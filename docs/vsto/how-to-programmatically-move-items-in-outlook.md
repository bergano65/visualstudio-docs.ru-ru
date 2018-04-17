---
title: 'Как: программное перемещение элементов в Outlook | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9eca20d533ba429db8b4227d5620c507fd805a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
  