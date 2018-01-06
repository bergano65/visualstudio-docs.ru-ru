---
title: "Как: программный поиск в определенной папке | Документы Microsoft"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], searching
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6397f6e90423640697aa57d7fdf2a1c85303d0f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Практическое руководство. Программный поиск в указанной папке
  Этот пример кода использует `Find` и `FindNext` методы для поиска текста в поле темы сообщения электронной почты, которые в **папки "Входящие"**. Этот метод использует фильтр строк для поиска буквы T букве из `Subject` текста.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Общие сведения о модели объектов Outlook](../vsto/outlook-object-model-overview.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  