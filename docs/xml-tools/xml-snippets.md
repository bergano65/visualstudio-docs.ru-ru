---
title: XML-фрагменты
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807728"
---
# <a name="xml-snippets"></a>XML-фрагменты

XML editor содержит возможность, называемую *XML-фрагменты*, который позволяет более быстро создавать XML-файлы. XML-фрагменты можно использовать повторно, вставляя их в файлы. Можно также создать XML-данные, основанные на схему языка определения схемы XML.

## <a name="reusable-xml-snippets"></a>Повторно используемые XML-фрагменты

XML editor включает множество фрагментов, охватывающих некоторые распространенные задачи. Это позволяет более легко создавать XML-файлы. Например при создании или редактировании XML-схемы, с помощью фрагментов «Элемент последовательности сложного типа» и «Элемент простого типа» вставляет следующий текст XML в файл. Затем при необходимости можно изменить значение `name`.

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

Существует два способа вставки фрагментов. **Вставить фрагмент** команда вставляет фрагмент кода XML в позиции курсора. **Окружить** команда создает оболочку для XML-фрагмент вокруг выбранного текста. Обе команды доступны либо из **IntelliSense** подменю **изменить** меню или из контекстного меню в редакторе.

Дополнительные сведения см. в разделе [Как Использовать XML-фрагменты](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>XML-фрагменты, сформированные схемой

Редактор XML также имеет возможность создания XML-фрагмент из схемы XML. Эта функция позволяет заполнять элементы XML-элементами, созданными из информации схемы для этого элемента. Дополнительные сведения см. в разделе [Как Создание XML-фрагмент из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Создание нового XML-фрагментов

Кроме фрагментов, которые входят в состав Visual Studio по умолчанию можно также создать и использовать собственные XML-фрагменты. Дополнительные сведения см. в разделе [Как Создание XML-фрагментов](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>См. также

- [Фрагменты кода в Visual Studio](../ide/code-snippets.md)
- [Редактор XML](../xml-tools/xml-editor.md)