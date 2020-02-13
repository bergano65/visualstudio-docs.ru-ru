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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3198b94b1248f20b178e85e9e75a2765e6191c28
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586306"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

Доступ к XML-данным в наборе данных осуществляется путем вызова доступных методов XML в наборе данных. Чтобы сохранить данные в формате XML, можно вызвать либо метод <xref:System.Data.DataSet.GetXml%2A>, либо метод <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet>.

Вызов метода <xref:System.Data.DataSet.GetXml%2A> возвращает строку, содержащую данные из всех таблиц данных в наборе данных, отформатированном как XML.

При вызове метода <xref:System.Data.DataSet.WriteXml%2A> данные в формате XML отправляются в указанный файл.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Сохранение данных в наборе данных в виде XML-файла в переменную

- Метод <xref:System.Data.DataSet.GetXml%2A> возвращает значение <xref:System.String>. Объявите переменную типа <xref:System.String> и присвойте ей результаты метода <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Сохранение данных в наборе данных в виде XML-файла

- Метод <xref:System.Data.DataSet.WriteXml%2A> имеет несколько перегрузок. Объявите переменную и присвойте ей допустимый путь для сохранения файла. В следующем примере кода показано, как сохранить данные в файл:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>См. также:

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
