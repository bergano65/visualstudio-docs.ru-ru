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
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533241"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062. Проверьте аргументы или открытые методы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Внешний видимый метод разыменование одного из ссылочных аргументов без проверки того, является ли этот аргумент `null` ( `Nothing` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 Все ссылочные аргументы, которые передаются в методы, видимые извне, должны проверяться по отношению к `null` . При необходимости вызовите исключение, если <xref:System.ArgumentNullException> аргумент имеет значение `null` .

 Если метод может быть вызван из неизвестной сборки, так как он объявлен как открытый или защищенный, следует проверить все параметры метода. Если метод предназначен для вызова только известными сборками, необходимо сделать метод внутренним и применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> атрибут к сборке, содержащей метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, проверьте каждый аргумент ссылки на `null` .

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
 Конструкторы копий, заполняющие поля или свойства, являющиеся ссылочными объектами, также могут нарушать правило CA1062. Нарушение возникает из-за того, что копируемый объект, передаваемый в конструктор копирования, может быть `null` ( `Nothing` в Visual Basic). Чтобы устранить нарушение, используйте статический метод (Shared в Visual Basic), чтобы убедиться, что скопированный объект не имеет значение null.

 В следующем `Person` примере класса `other` объект, который передается в `Person` конструктор копии, может иметь значение `null` .

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
 В следующем исправленном `Person` примере `other` объект, который передается в конструктор копии, сначала проверяется на значение NULL в `PassThroughNonNull` методе.

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
