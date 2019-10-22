---
title: 'CA1062: проверка аргументов открытых методов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663643"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: проверьте аргументы открытых методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод, видимый извне, отменяет ссылку на один из ссылочных аргументов, не проверяя, является ли этот аргумент `null` (`Nothing` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 Все ссылочные аргументы, которые передаются в методы, видимые извне, должны проверяться по `null`. При необходимости вызовите <xref:System.ArgumentNullException>, если аргумент имеет значение `null`.

 Если метод может быть вызван из неизвестной сборки, так как он объявлен как открытый или защищенный, следует проверить все параметры метода. Если метод предназначен для вызова только известными сборками, необходимо сделать метод внутренним и применить атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> к сборке, содержащей метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, проверьте каждый ссылочный аргумент на `null`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы уверены, что параметр разыменования был проверен другим вызовом метода в функции.

## <a name="example"></a>Пример
 В следующем примере показан метод, нарушающий правило, и метод, который удовлетворяет правилу.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Пример
 В [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] это правило не обнаруживает, что параметры передаются другому методу, выполняющему проверку.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Пример
 Конструкторы копий, заполняющие поля или свойства, являющиеся ссылочными объектами, также могут нарушать правило CA1062. Нарушение возникает из-за того, что копируемый объект, передаваемый в конструктор копирования, может быть `null` (`Nothing` в Visual Basic). Чтобы устранить нарушение, используйте статический метод (Shared в Visual Basic), чтобы убедиться, что скопированный объект не имеет значение null.

 В следующем примере класса `Person` объект `other`, который передается в конструктор копии `Person`, может быть `null`.

```

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Пример
 В следующем исправленном `Person` объект `other`, который передается в конструктор копии, сначала проверяется на значение NULL в методе `PassThroughNonNull`.

```
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```
