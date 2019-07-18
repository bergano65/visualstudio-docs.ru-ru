---
title: Практическое руководство. Использование конструктора схем XML с XML-литералами
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9e92cbdca3ac2c5c366ec054ba79f2e7324986c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001816"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Практическое руководство. Использование конструктора схем XML с литералами XML

В этом разделе описывается процесс просмотра схемы, связанной с XML-литералом в проекте Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Создайте новый проект Visual Basic

1. Запустите Visual Studio.

2. Создать новый Visual Basic **консольное приложение** проект с именем **XMLLiterals**.

     Новый проект содержит один исходный файл Visual Basic, *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Добавление существующего XSD-файла

1. Откройте новый текстовый файл в блокноте. Скопируйте образец кода XML-схемы из [схема заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.

2. Сохраните файл в любом местоположении под именем *PurchaseOrderSchema.xsd*.

3. В **обозревателе решений**, щелкните правой кнопкой мыши имя проекта, выберите **добавить**, а затем выберите **существующий элемент**. **Добавить существующий элемент** откроется диалоговое окно. Перейдите к *PurchaseOrderSchema.xsd* файл, выберите его и нажмите кнопку **добавить**.

     Проект XMLLiterals теперь содержит два файла: *Module1.vb* и *PurchaseOrderSchema.xsd*.

## <a name="add-code"></a>Добавление кода

Добавление кода Visual Basic с помощью XML-литерала, на основании XSD-файл, включенный в проект:

1. Замените код в *Module1.vb* файла следующим кодом:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Щелкните правой кнопкой мыши любой узел XML в XML-литерале или импорте пространства имен XML и выберите **Показать в обозревателе схем**.

   **Обозреватель XML-схем** будет отображен файл Visual Basic с XML-литерал, связанный с набором схемы XML.