---
title: Фрагменты XML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669363"
---
# <a name="xml-snippets"></a>XML-фрагменты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор XML предлагает функцию, называемую *XML-фрагментами*, которая позволяет быстрее создавать XML-файлы. XML-фрагменты можно использовать повторно, вставляя их в файлы. Также можно создавать XML-данные, исходя из схемы на языке XSD.

## <a name="reusable-xml-snippets"></a>Повторно используемые XML-фрагменты
 XML Editor включает множество фрагментов, охватывающих некоторые распространенные задачи. Это позволяет более легко создавать XML-файлы. Например, при создании или редактировании XML-схемы с помощью фрагментов «Элемент последовательности сложного типа» и «Элемент простого типа» в файл вставляется следующий текст XML. Затем при необходимости можно изменить значение `name`.

```
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

 Существует два способа вставки фрагментов. Команда **Вставить фрагмент** вставляет XML-фрагмент в позицию курсора. Команда **окружить с помощью** оболочки фрагмента кода XML вокруг выделенного текста. Обе команды доступны либо из подменю **IntelliSense** в меню **Правка** , либо из контекстного меню редактора.

 Дополнительные сведения см. [в разделе Практические руководства. Использование XML-фрагментов](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>XML-фрагменты, сформированные схемой
 XML Editor также может создавать XML-фрагменты из XML-схем. Эта функция позволяет заполнять элементы XML-элементами, созданными из информации схемы для этого элемента.

 Дополнительные сведения см. [в разделе инструкции. Создание XML-фрагмента из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Создание новых XML-фрагментов
 В дополнение к фрагментам, которые включены в [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio по умолчанию, можно также создавать и использовать собственные XML-фрагменты.

 Дополнительные сведения см. [в разделе инструкции. Создание XML-фрагментов](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>См. также раздел
 [XML-редактор](../xml-tools/xml-editor.md)
