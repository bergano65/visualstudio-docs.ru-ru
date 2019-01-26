---
title: Как выполнить Программное связывание веб-страницы с папкой Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c60ac58c59adaacd66a7c56b4c394d596cfd6b24
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871277"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Как выполнить Программное связывание веб-страницы с папкой Outlook
  В этом примере проверяется для папки с именем `HtmlView` в Microsoft Office Outlook. Если папка не существует, код создает папку и присваивает ему веб-страницы. Если папка существует, код отображает содержимое папки.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>См. также  
 [Работа с папками](../vsto/working-with-folders.md)   
 [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Практическое руководство. Программное создание настраиваемых элементов папок](../vsto/how-to-programmatically-create-custom-folder-items.md)  
