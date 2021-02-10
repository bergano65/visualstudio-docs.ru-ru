---
title: Как программно получить папку по имени
description: Узнайте, как можно использовать Visual Studio для программного извлечения папки по имени и последующего отображения содержимого папки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c05f8bc0174807a5336a9d9f79ac3dc81e87476e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953881"
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
