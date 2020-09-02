---
title: Руководство. Программный поиск в определенной папке
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8f5e0f098edcffce07eb2c3f243b994d1a53cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547021"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Руководство. Программный поиск в определенной папке
  В этом примере кода используются `Find` `FindNext` методы и для поиска текста в поле subject сообщений электронной почты, которые находятся в **папке Входящие**. Этот метод использует фильтр строк для проверки буквы T в качестве начальной буквы `Subject` текста.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>См. также раздел
- [Работа с папками](../vsto/working-with-folders.md)
- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
