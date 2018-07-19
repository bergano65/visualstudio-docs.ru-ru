---
title: 'Практическое: программное перемещение элементов в Outlook'
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
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257726"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Практическое: программное перемещение элементов в Outlook
  В этом примере перемещает непрочитанные сообщения электронной почты из **папки "Входящие"** в папку с именем **теста**. В примере перемещается только сообщения, которые содержат слово **теста** в `Subject` поля.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   Папка почты Outlook с именем **теста**.  
  
-   Сообщение электронной почты с слово **теста** в `Subject` поля.  
  
## <a name="see-also"></a>См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Практическое: программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое: программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Практическое: программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  