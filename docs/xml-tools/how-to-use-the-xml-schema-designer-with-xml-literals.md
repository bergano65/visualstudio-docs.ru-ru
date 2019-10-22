---
title: Как использовать конструктор XML-схем с XML-литералами
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: ed987a54004004fe8c4fbfba686ae1a35d12bb06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601854"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Как использовать конструктор XML-схем с XML-литералами

В этом разделе описывается процесс просмотра схемы, связанной с XML-литералом в проекте Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Создание нового проекта Visual Basic

1. Запустите Visual Studio.

2. Создайте новый проект Visual Basic **консольное приложение** с именем **ксмллитералс**.

     Новый проект содержит один Visual Basic исходный файл, *Module1. vb*.

## <a name="add-an-existing-xsd-file"></a>Добавление существующего XSD-файла

1. Откройте новый текстовый файл в блокноте. Скопируйте образец кода XML-схемы из [схемы заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.

2. Сохраните файл в определенном расположении с именем *пурчасеордерсчема. xsd*.

3. В **Обозреватель решений**щелкните правой кнопкой мыши имя проекта, выберите **Добавить**, а затем выберите **существующий элемент**. Откроется диалоговое окно **элемент аддексистинг** . Перейдите к файлу *пурчасеордерсчема. xsd* , выберите его и нажмите кнопку **Добавить**.

     Проект Ксмллитералс теперь содержит два файла: *Module1. vb* и *пурчасеордерсчема. xsd*.

## <a name="add-code"></a>Добавить код

Чтобы добавить Visual Basicный код с литералом XML, на основе XSD-файла, включенного в проект:

1. Замените код в файле *Module1. vb* следующим кодом:

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

2. Щелкните правой кнопкой мыши любой XML-узел в XML-литерале или импорте пространства имен XML и выберите пункт **отобразить в обозревателе схем**.

   **Обозреватель XML-схем** отображается параллельно с Visual Basicным файлом, имеющим XML-литерал, связанный с набором схем XML.