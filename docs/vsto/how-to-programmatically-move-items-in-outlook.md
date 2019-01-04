---
title: Как выполнить Программное перемещение элементов в Outlook
ms.date: 02/02/2017
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
ms.openlocfilehash: 51123937fd26b6d6decf3770affd83b1d58d5bfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875745"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Как выполнить Программное перемещение элементов в Outlook
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
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программный поиск в указанной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Практическое руководство. Программное выполнение действий при получении сообщения электронной почты](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
