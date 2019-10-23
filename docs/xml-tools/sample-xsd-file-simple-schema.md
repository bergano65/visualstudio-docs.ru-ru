---
title: 'Образец XSD-файла: Простая схема'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b6681e47ba33d16cd48f5f34389a5d113fc36ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651162"
---
# <a name="sample-xsd-file-simple-schema"></a>Образец XSD-файла: Простая схема

Следующий файл XSD используется в различных примерах документации конструктора схем XSD. Этот файл представляет собой простую схему заказа на покупку.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными. Любые совпадения с реальными предприятиями, организациями, товарами, именами доменов, адресами электронной почты, эмблемами, лицами, местами и событиями являются случайными и непреднамеренными.