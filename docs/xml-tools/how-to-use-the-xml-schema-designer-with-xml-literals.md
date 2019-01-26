---
title: Как выполнить Использование конструктора схем XML с XML-литералами
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3883b4515ab304e2a247414f63c79db6314a654c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922082"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Как выполнить Использовать конструктор XML-схем с XML-литералами

В этом разделе описывается процесс просмотра схемы, связанной с XML-литералом в проекте Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Создание нового проекта приложения командной строки Visual Basic

1.  Запустите Visual Studio.

2.  Из **файл** меню, выберите **New**, а затем выберите **проекта**. Откроется диалоговое окно **Новый проект** . Для **типы проектов**выберите **другие языки** , а затем выберите **Visual Basic**. Для **шаблоны**, выберите консольное приложение. Затем введите `XMLLiterals` в **имя** поля и расположение проекта в **расположение** поля. Нажмите кнопку **ОК**.

     Создан новый проект. Проект XMLLiterals содержит один исходный файл Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Добавление существующего XSD-файла в проект

1.  Откройте новый текстовый файл в блокноте. Скопируйте образец кода XML-схемы из [схема заказа на покупку](../xml-tools/sample-xsd-file-simple-schema.md) и вставьте его в файл.

2.  Сохраните файл в любом местоположении под именем *PurchaseOrderSchema.xsd*.

3.  В **обозревателе решений**, щелкните правой кнопкой мыши имя проекта, выберите **добавить**, а затем выберите **существующий элемент**. **Добавить существующий элемент** откроется диалоговое окно. Перейдите к *PurchaseOrderSchema.xsd* файл, выберите его и нажмите кнопку **добавить**.

     Проект XMLLiterals теперь содержит два файла: *Module1.vb* и *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Добавление кода Visual Basic с XML-литералом на основе XSD-файла, включенного в проект

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