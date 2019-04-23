---
title: XML-фрагменты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e2fbba9006c1621b8f98084d4ffd4c637be1127
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654659"
---
# <a name="xml-snippets"></a>XML-фрагменты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Editor содержит возможность, называемую *XML-фрагменты*, который позволяет более быстро создавать XML-файлы. XML-фрагменты можно использовать повторно, вставляя их в файлы. Также можно создавать XML-данные, исходя из схемы на языке XSD.  
  
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
  
 Существует два способа вставки фрагментов. **Вставить фрагмент** команда вставляет фрагмент кода XML в позиции курсора. **Окружить** команда создает оболочку для XML-фрагмент вокруг выбранного текста. Обе команды доступны либо из **IntelliSense** подменю **изменить** меню или в контекстном меню редактора.  
  
 Дополнительные сведения см. в разделе [Как Использовать XML-фрагменты](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>XML-фрагменты, сформированные схемой  
 XML Editor также может создавать XML-фрагменты из XML-схем. Эта функция позволяет заполнять элементы XML-элементами, созданными из информации схемы для этого элемента.  
  
 Дополнительные сведения см. в разделе [Как Создание XML-фрагмент из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Создание новых XML-фрагментов  
 Кроме фрагментов, которые входят в состав [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio по умолчанию, можно также создать и использовать собственные XML-фрагменты.  
  
 Дополнительные сведения см. в разделе [Как Создание XML-фрагментов](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>См. также  
 [XML-редактор](../xml-tools/xml-editor.md)
