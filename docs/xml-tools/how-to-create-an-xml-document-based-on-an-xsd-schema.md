---
title: Как создать XML-документ на основе XSD-схемы
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d3da2e6b5b0c9ea2701524c0fb2fde1e1313687
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Как: создать XML-документ, на основе схемы XSD

**Создание образца XML** функция создает образец XML-файла на основе вашего файла схемы XML (XSD).

 Этот пункт можно использовать в следующих случаях.

-   Чтобы понять, как использовать различные конструкции в данной схеме.

-   Чтобы убедиться в том, что схема функционирует должным образом.

**Создание образца XML** компонент доступен только для глобальных элементов и требует набор схем XML был допустимым.

С помощью этой возможности обычно создаются допустимые XML-документы. Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.

-   Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.

-   Аспекты `xs:pattern`.

-   Перечисления типа `xs:QName`.

-   Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.

Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Создание экземпляра XML-документа на основе XSD-файла.

1.  Следуйте указаниям в [как: Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  В [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md), щелкните правой кнопкой мыши `PurchaseOrder` глобального элемента. Выберите **Создание образца XML**.

     При выборе этого параметра PurchaseOrder. *xml* файл следующий образец XML-содержимого, которые будут создаваться и открывается в редакторе XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>См. также

- [Работа с XML-данных](../xml-tools/working-with-xml-data.md)