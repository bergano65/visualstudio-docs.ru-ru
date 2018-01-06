---
title: "Сохранение набора данных в формате XML | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c6176b1d7e9f18ce08fddf21f199cd21304ca8a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML
XML-данные в наборе данных может осуществляться путем вызова доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать <xref:System.Data.DataSet.GetXml%2A> метода или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.  
  
 Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который имеет формат XML.  
  
 Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет данные в формате XML в файл, который задается.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранить данные в наборе данных в виде XML в переменную  
  
-   <xref:System.Data.DataSet.GetXml%2A> Возвращает <xref:System.String>. Это означает, что объявить переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Для сохранения данных в наборе данных в формате XML в файл  
  
-   <xref:System.Data.DataSet.WriteXml%2A> Метода есть несколько перегрузок. Ниже показано, как сохранить данные в файл. Объявить переменную и присвоить ему допустимый путь для сохранения файла.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)