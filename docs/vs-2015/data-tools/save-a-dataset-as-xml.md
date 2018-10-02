---
title: Сохранение набора данных в формате XML | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfea6a97dd5126216d5163dee1dc17e5f6364b46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557942"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сохранение набора данных в формате XML](https://docs.microsoft.com/visualstudio/data-tools/save-a-dataset-as-xml).  
  
  
XML-данные в наборе данных может осуществляться путем вызова доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.  
  
 Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который представлен в виде XML.  
  
 Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет XML-данных в файл вами.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранять данные в наборе данных в виде XML в переменную  
  
-   <xref:System.Data.DataSet.GetXml%2A> Возвращает метод <xref:System.String>. Это означает, что вы объявляете переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Чтобы сохранить данные в наборе данных в виде XML в файл  
  
-   <xref:System.Data.DataSet.WriteXml%2A> Метод имеет несколько перегрузок. Следующий код демонстрирует способы сохранения данных в файл. Объявите переменную и назначьте его допустимый путь для сохранения файла.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

