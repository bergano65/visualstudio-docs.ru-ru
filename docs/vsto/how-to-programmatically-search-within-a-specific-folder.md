---
title: Практическое руководство. Программный поиск в указанной папке
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961905"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Практическое руководство. Программный поиск в указанной папке
  Данный пример кода использует `Find` и `FindNext` методы для поиска текста в поле темы сообщения электронной почты, которые в **папки "Входящие"**. Этот метод использует фильтр строк для поиска букву T букве из `Subject` текста.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
