---
title: Практическое руководство. Создание XML-документа на основе схемы XSD
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424b325b244499a18077cc1df0ff9164c41763d2
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815465"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Практическое руководство. Создание XML-документа на основе схемы XSD

Функция **Создание образца XML** создает образец XML-файла на основании файла XML-схемы (XSD).

Этот пункт можно использовать в следующих случаях.

- Чтобы понять, как использовать различные конструкции в данной схеме.

- Чтобы убедиться в том, что схема функционирует должным образом.

Функция **Создание образца XML** доступна только для глобальных элементов и требует, чтобы набор схем XML был допустимым.

С помощью этой функции обычно создаются допустимые XML-документы. Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.

- Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.

- Аспекты `xs:pattern`.

- Перечисления типа `xs:QName`.

- Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.

Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Создание экземпляра XML-документа на основе XSD-файла.

1. Выполните действия, описанные в статье [Практическое руководство. Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. В [обозревателе XML-схем](../xml-tools/xml-schema-explorer.md) щелкните правой кнопкой мыши глобальный элемент `PurchaseOrder`. Выберите **Создание образца XML**.

     Если выбран данный параметр, файл PurchaseOrder.*xml* со следующим образцом XML-содержимого будет создан и открыт в редакторе XML:

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
