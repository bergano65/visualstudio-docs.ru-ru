---
title: Практическое руководство. Создание XML-документа на основе схемы XSD
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7739f33bad62667fdc7be8704237ebdd3932739c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918565"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Практическое руководство. Создание XML-документа на основе схемы XSD

Функция **создания примера XML** создает пример XML-файла на основе файла схемы XML (XSD).

Этот пункт можно использовать в следующих случаях.

- Чтобы понять, как использовать различные конструкции в данной схеме.

- Чтобы убедиться в том, что схема функционирует должным образом.

Функция **создания образца XML** доступна только для глобальных элементов и требует наличия допустимого набора XML-схем.

С помощью этой функции обычно создаются допустимые XML-документы. Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.

- Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.

- Аспекты `xs:pattern`.

- Перечисления типа `xs:QName`.

- Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.

Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Создание экземпляра XML-документа на основе XSD-файла.

1. Выполните действия, описанные в разделе [как: Создание и изменение файла](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)XSD-схемы.

2. В [обозревателе XML-схем](../xml-tools/xml-schema-explorer.md)щелкните правой кнопкой мыши `PurchaseOrder` глобальный элемент. Выберите **создать образец XML**.

     При выборе этого параметра PurchaseOrder. *XML-* файл со следующим ОБРАЗЦом XML-содержимого будет создан и открыт в редакторе XML:

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