---
title: 'CA2240: Реализуйте ISerializable правильно | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 08c383f42e7667a3f822298c14f29e81d22a309b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591636"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: правильно реализуйте ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2240: реализуйте ISerializable правильно](https://docs.microsoft.com/visualstudio/code-quality/ca2240-implement-iserializable-correctly).

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип может быть назначен для <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и одну из следующих условий верно:

-   Тип наследуется, но не переопределяет <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод и тип объявляет поля экземпляра, которые не помечены <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибута.

-   Тип не является запечатанным и тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод, который не является внешней и переопределяемым.

## <a name="rule-description"></a>Описание правила
 Поля, объявленные в тип, наследующий экземпляров <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейса не добавляются автоматически в процессе сериализации. Чтобы включить поля, тип должен реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и конструктор сериализации. Если поля не должны быть сериализованы, примените <xref:System.NonSerializedAttribute> атрибут для поля, чтобы явно указать решение.

 В типах, которые не являются запечатанными, реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод должен быть видимый извне. Таким образом метод может вызываться с помощью производных типов и переопределяемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены с <xref:System.NonSerializedAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два сериализуемые типы, которые нарушают данное правило.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере устраняется двух предыдущих нарушений, предоставляя можно переопределить реализацию [ISerializable.GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) в классе книги, а также предоставляя реализацию <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> библиотеки класса.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)



