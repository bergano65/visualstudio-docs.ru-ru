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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c993ac8703468a24a99e114563fec1bdc817581
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566232"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

Получить доступ к XML-данные в наборе данных, вызвав доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.

Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который представлен в виде XML.

Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет XML-данных в файл вами.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранять данные в наборе данных в виде XML в переменную

- Метод <xref:System.Data.DataSet.GetXml%2A> возвращает значение <xref:System.String>. Объявите переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Чтобы сохранить данные в наборе данных в виде XML в файл

- <xref:System.Data.DataSet.WriteXml%2A> Метод имеет несколько перегрузок. Объявите переменную и назначьте его допустимый путь для сохранения файла. Следующий код демонстрирует способы сохранения данных в файл:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)