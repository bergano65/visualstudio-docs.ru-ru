---
title: Сохранение набора данных в формате XML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 2e4331b59c532e681c7e10ab8e43b953e9f72b18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559572"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML-данные в наборе данных может осуществляться путем вызова доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.  
  
 Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который представлен в виде XML.  
  
 Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет XML-данных в файл вами.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранять данные в наборе данных в виде XML в переменную  
  
- <xref:System.Data.DataSet.GetXml%2A> Возвращает метод <xref:System.String>. Это означает, что вы объявляете переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Чтобы сохранить данные в наборе данных в виде XML в файл  
  
- <xref:System.Data.DataSet.WriteXml%2A> Метод имеет несколько перегрузок. Следующий код демонстрирует способы сохранения данных в файл. Объявите переменную и назначьте его допустимый путь для сохранения файла.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
