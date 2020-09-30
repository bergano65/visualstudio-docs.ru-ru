---
title: Связывание веб-страницы с папкой Outlook
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 35eb2dc3b1b595a4bf960af67ac5006cd9839c6e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585344"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Связывание веб-страницы с папкой Outlook

  В этом примере проверяется наличие папки с именем `HtmlView` в Microsoft Office Outlook. Если папка не существует, код создает папку и назначает ей веб-страницу. Если папка существует, в коде отображается содержимое папки.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>См. также
- [Работа с папками](../vsto/working-with-folders.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программное создание пользовательских элементов папки](../vsto/how-to-programmatically-create-custom-folder-items.md)
