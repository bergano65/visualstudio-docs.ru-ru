---
title: XML-фрагменты
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592325"
---
# <a name="xml-snippets"></a>XML-фрагменты

Редактор XML предлагает функцию, называемую *XML-фрагментами*, которая позволяет быстрее создавать XML-файлы. XML-фрагменты можно использовать повторно, вставляя их в файлы. Можно также создавать XML-данные на основе схемы языка определения схемы XML (XSD).

## <a name="reusable-xml-snippets"></a>Многократно используемые XML-фрагменты

Редактор XML содержит много фрагментов кода, охватывающих некоторые распространенные задачи. Это позволяет более легко создавать XML-файлы. Например, при создании схемы XML с помощью фрагментов "сложный элемент последовательности" и "элемент простого типа" вставляет следующий XML-текст в файл. Затем при необходимости можно изменить значение `name`.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Существует два способа вставки фрагментов. Команда **Вставить фрагмент** вставляет XML-фрагмент в позицию курсора. Команда **окружить с помощью** оболочки фрагмента кода XML вокруг выделенного текста. Обе команды доступны либо из подменю **IntelliSense** в меню **Правка** , либо из контекстного меню в редакторе.

Дополнительные сведения см. [в разделе Практические руководства. Использование XML-фрагментов](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>XML-фрагменты, сформированные схемой

XML-редактор также может создавать XML-фрагменты из схемы XML. Эта функция позволяет заполнять элементы XML-элементами, созданными из информации схемы для этого элемента. Дополнительные сведения см. [в разделе инструкции. Создание XML-фрагмента из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Создание новых XML-фрагментов

В дополнение к фрагментам, которые включены в Visual Studio по умолчанию, можно также создавать и использовать собственные XML-фрагменты. Дополнительные сведения см. [в разделе инструкции. Создание XML-фрагментов](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>См. также:

- [Фрагменты кода в Visual Studio](../ide/code-snippets.md)
- [Редактор XML](../xml-tools/xml-editor.md)
