---
title: 'Образец XSD-файла: Отношения'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e5d335fb6f90e6e93d58013958e94f6d4555c39
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65455098"
---
# <a name="sample-xsd-file-relationships"></a>Образец XSD-файла: Отношения

Следующий файл XSD используется в различных примерах документации конструктора схем XSD. Данный файл является схемой типичного заказа на покупку, включающей заметки и документацию.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="pet" type="PetType"/>

  <xs:attributeGroup name="NameAgeAttributes">
    <xs:attribute name="age" type="xs:integer" use="required"/>
    <xs:attribute name="name" type="xs:string" use="required"/>
  </xs:attributeGroup>

  <xs:complexType name="PetType">
    <xs:attributeGroup ref="NameAgeAttributes"/>
  </xs:complexType>

  <xs:element name="cat" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

  <xs:element name="dog" substitutionGroup="pet">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="PetType">
          <xs:sequence>
            <xs:element name="weight" type="xs:integer"/>
            <xs:element name="color" type="xs:string"/>
            <xs:element name="breed" type="xs:integer"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>

</xs:schema>
```

> [!NOTE]
> Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными. Любые совпадения с реальными предприятиями, организациями, товарами, именами доменов, адресами электронной почты, эмблемами, лицами, местами и событиями являются случайными и непреднамеренными.