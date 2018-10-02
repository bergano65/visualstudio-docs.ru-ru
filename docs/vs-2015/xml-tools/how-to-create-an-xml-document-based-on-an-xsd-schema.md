---
title: 'Практическое: Создание XML-документа на основе схемы XSD | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ce870506097c820d5a6a8e981ffd63d64257780
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559043"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Как создать XML-документ на основе XSD-схемы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Создание документа XML на основе на схему XSD](https://docs.microsoft.com/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema).  
  
  
**Создание образца XML** функция создает пример XML-файла, на базе файла схемы XML (XSD).  
  
 Этот пункт можно использовать в следующих случаях.  
  
-   Чтобы понять, как использовать различные конструкции в данной схеме.  
  
-   Чтобы убедиться в том, что схема функционирует должным образом.  
  
 **Создание образца XML** компонент доступен только для глобальных элементов и требует допустимый набор схем XML.  
  
 С помощью этой возможности обычно создаются допустимые XML-документы. Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.  
  
-   Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.  
  
-   Аспекты `xs:pattern`.  
  
-   Перечисления типа `xs:QName`.  
  
-   Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.  
  
 Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Создание экземпляра XML-документа на основе XSD-файла.  
  
1.  Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В [обозреватель XML-схем](../xml-tools/xml-schema-explorer.md), щелкните правой кнопкой мыши `PurchaseOrder` глобального элемента. Выберите **Создание образца XML**.  
  
     Если выбран данный параметр, файл PurchaseOrder.xml со следующим образцом XML-содержимого будет создан и открыт в редакторе XML:  
  
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
  
## <a name="see-also"></a>См. также  
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md)



