---
title: Практическое руководство. Программное связывание веб-страницы с папкой Outlook
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
ms.openlocfilehash: e83f8b7f6bcdb790b5e545aa76426bc05f0735f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817313"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Практическое руководство. Программное связывание веб-страницы с папкой Outlook
  В этом примере проверяется для папки с именем `HtmlView` в Microsoft Office Outlook. Если папка не существует, код создает папку и присваивает ему веб-страницы. Если папка существует, код отображает содержимое папки.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Практическое руководство. Программное извлечение папки по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Практическое руководство. Программное создание настраиваемых элементов папок](../vsto/how-to-programmatically-create-custom-folder-items.md)
