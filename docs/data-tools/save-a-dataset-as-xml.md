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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a1b0c453f3b48b12c5a77fce86789a66fe77c26
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174001"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML

Получить доступ к XML-данные в наборе данных, вызвав доступные методы XML для набора данных. Чтобы сохранить данные в формате XML, можно вызвать либо <xref:System.Data.DataSet.GetXml%2A> метод или <xref:System.Data.DataSet.WriteXml%2A> метод <xref:System.Data.DataSet>.

Вызов <xref:System.Data.DataSet.GetXml%2A> метод возвращает строку, содержащую данные из всех таблиц в наборе данных, который представлен в виде XML.

Вызов <xref:System.Data.DataSet.WriteXml%2A> метод отправляет XML-данных в файл вами.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Чтобы сохранять данные в наборе данных в виде XML в переменную

- <xref:System.Data.DataSet.GetXml%2A> Возвращает метод <xref:System.String>. Объявите переменную типа <xref:System.String> и назначьте его результаты <xref:System.Data.DataSet.GetXml%2A> метод.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Чтобы сохранить данные в наборе данных в виде XML в файл

- <xref:System.Data.DataSet.WriteXml%2A> Метод имеет несколько перегрузок. Объявите переменную и назначьте его допустимый путь для сохранения файла. Следующий код демонстрирует способы сохранения данных в файл:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)