---
title: Сохранение набора данных в формате XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b384c7d2042611be84322fd5a842f1ba5ca8de9c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

XML-данные в наборе данных может осуществляться путем вызова доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать <xref:System.Data.DataSet.GetXml%2A> метода или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.

Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который имеет формат XML.

Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет данные в формате XML в файл, который задается.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранить данные в наборе данных в виде XML в переменную

- <xref:System.Data.DataSet.GetXml%2A> Возвращает <xref:System.String>. Объявите переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Для сохранения данных в наборе данных в формате XML в файл

- <xref:System.Data.DataSet.WriteXml%2A> Метода есть несколько перегрузок. Объявить переменную и присвоить ему допустимый путь для сохранения файла. Ниже показано, как сохранить данные в файл:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)