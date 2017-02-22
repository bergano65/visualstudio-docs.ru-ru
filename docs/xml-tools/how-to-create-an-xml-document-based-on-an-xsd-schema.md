---
title: "Как создать XML-документ на основе XSD-схемы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Как создать XML-документ на основе XSD-схемы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Функция **Создание образца XML** создает образец XML\-файла на основании файла XML\-схемы \(XSD\).  
  
 Этот параметр можно использовать в следующих случаях.  
  
-   Чтобы понять, как использовать различные конструкции в данной схеме.  
  
-   Чтобы убедиться в том, что схема функционирует должным образом.  
  
 Функция **Generate Sample XML** \(Создание образца XML\) доступна только для глобальных элементов и требует, чтобы набор схем XML был допустимым.  
  
 С помощью этой функции обычно создаются допустимые XML\-документы.Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.  
  
-   Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.  
  
-   Аспекты `xs:pattern`.  
  
-   Перечисления типа `xs:QName`.  
  
-   Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.  
  
 Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.  
  
### Создание экземпляра XML\-документа на основе XSD\-файла.  
  
1.  Следуйте шагам, описанным в разделе [Как создавать и изменять файл XSD\-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В [Обозревателе XML\-схем](../xml-tools/xml-schema-explorer.md) щелкните правой кнопкой мыши глобальный элемент `PurchaseOrder`.Выберите **Создание образца XML**.  
  
     Если выбран данный параметр, файл PurchaseOrder.xml со следующим образцом XML\-содержимого будет создан и открыт в редакторе XML:  
  
    ```  
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
  
## См. также  
 [Работа с XML\-данными](../xml-tools/working-with-xml-data.md)