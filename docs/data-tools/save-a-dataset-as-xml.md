---
title: Сохранение набора данных в формате XML
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: cc8854581903ab58a327ff18be7b3b7c0f860a3b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281738"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

Доступ к XML-данным в наборе данных осуществляется путем вызова доступных методов XML в наборе данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод, либо <xref:System.Data.DataSet.WriteXml%2A> метод объекта <xref:System.Data.DataSet> .

При вызове <xref:System.Data.DataSet.GetXml%2A> метода возвращается строка, содержащая данные из всех таблиц данных в наборе данных, отформатированном как XML.

При вызове <xref:System.Data.DataSet.WriteXml%2A> метода данные в формате XML отправляются в указанный файл.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Сохранение данных в наборе данных в виде XML-файла в переменную

- Метод <xref:System.Data.DataSet.GetXml%2A> возвращает значение <xref:System.String>. Объявите переменную типа <xref:System.String> и присвойте ей результаты <xref:System.Data.DataSet.GetXml%2A> метода.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Сохранение данных в наборе данных в виде XML-файла

- <xref:System.Data.DataSet.WriteXml%2A>Метод имеет несколько перегрузок. Объявите переменную и присвойте ей допустимый путь для сохранения файла. В следующем примере кода показано, как сохранить данные в файл:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
