---
title: 'Практическое: программный поиск в указанной папке'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64df4180e533f254927ae134ed005b0626dfdde8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674895"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Практическое: программный поиск в указанной папке
  Данный пример кода использует `Find` и `FindNext` методы для поиска текста в поле темы сообщения электронной почты, которые в **папки "Входящие"**. Этот метод использует фильтр строк для поиска букву T букве из `Subject` текста.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md)   
 [Практическое: программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  