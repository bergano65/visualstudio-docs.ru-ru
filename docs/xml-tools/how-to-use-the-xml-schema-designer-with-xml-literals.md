---
title: Практическое руководство. Использование конструктора схем XML с XML-литералами
description: Узнайте, как использовать конструктор XML-схем для просмотра схемы, связанной с XML-литералом в проекте Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: f233eaed4b08e499b3a7543d10caafd36c77a480
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969078"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Практическое руководство. Использование конструктора схем XML с литералами XML

В этом разделе описывается процесс просмотра схемы, связанной с XML-литералом в проекте Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Создание нового проекта Visual Basic

1. Запустите Visual Studio.

2. Создайте проект **консольного приложения** Visual Basic с именем **XMLLiterals**.

     Новый проект содержит один исходный файл Visual Basic — *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Добавление существующего XSD-файла

1. Откройте новый текстовый файл в Блокноте. Скопируйте пример кода XML-схемы из [схемы заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.

2. Сохраните файл под именем *PurchaseOrderSchema.xsd* в любом расположении.

3. В окне **Обозреватель решений** щелкните правой кнопкой мыши имя проекта, выберите элементы **Добавить** и **Существующий элемент**. Откроется диалоговое окно **Добавление существующего элемента**. Найдите файл *PurchaseOrderSchema.xsd*, выберите его и нажмите кнопку **Добавить**.

     Проект XMLLiterals теперь содержит два файла: *Module1.vb* и *PurchaseOrderSchema.xsd*.

## <a name="add-code"></a>Добавление кода

Чтобы добавить код Visual Basic с XML-литералом на основе XSD-файла, включенного в проект, сделайте следующее:

1. Замените код в файле *Module1.vb* следующим кодом:

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

2. Щелкните правой кнопкой мыши любой XML-узел в XML-литерале или импорте пространства имен XML и выберите пункт **Show in Schema Explorer** (Показать в обозревателе схем).

   **Обозреватель XML-схемы** будет отображен рядом с файлом Visual Basic, в котором есть XML-литерал, связанный с набором XML-схем.
