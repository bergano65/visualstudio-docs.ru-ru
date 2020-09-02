---
title: Как программно получить папку по имени
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 901de848b22f344ded2d71b11e9859917b8382d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547112"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Как программно получить папку по имени
  В этом примере возвращается ссылка на именованную пользовательскую папку, а затем отображается ее содержимое.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Папка с именем TestFolder.

## <a name="see-also"></a>См. также раздел
- [Работа с папками](../vsto/working-with-folders.md)
- [Руководство. Программный поиск в определенной папке](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Руководство. Программное создание пользовательских элементов папки](../vsto/how-to-programmatically-create-custom-folder-items.md)
