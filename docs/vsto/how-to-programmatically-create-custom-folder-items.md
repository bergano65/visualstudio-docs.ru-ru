---
title: Руководство. Программное создание пользовательских элементов папки
description: Сведения о программном создании пользовательских элементов папок в Microsoft Outlook с помощью Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: f149758665e5d7a7cdf7f4edd5d926e1de632dca
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527799"
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>Руководство. Программное создание пользовательских элементов папки
  В этом примере создается новая папка в Microsoft Office Outlook. Имя пользователя, вошедшего в систему, используется в качестве имени папки.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]

## <a name="see-also"></a>См. также раздел
- [Работа с папками](../vsto/working-with-folders.md)
- [Руководство. Программное добавление записи в контакты Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Руководство. Программное создание встреч](../vsto/how-to-programmatically-create-appointments.md)
