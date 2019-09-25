---
title: CA1062. Проверьте аргументы или открытые методы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8106a4c0244cbd79e88a2bdc50e04ea74627dab4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235341"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062. Проверьте аргументы или открытые методы

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Внешний видимый метод разыменование одного из ссылочных аргументов без проверки того, является `null` ли этот аргумент (`Nothing` в Visual Basic).

## <a name="rule-description"></a>Описание правила

Все ссылочные аргументы, которые передаются в методы, видимые извне `null`, должны проверяться по отношению к. При необходимости вызовите исключение <xref:System.ArgumentNullException> , если аргумент имеет `null`значение.

Если метод может быть вызван из неизвестной сборки, так как он объявлен как открытый или защищенный, следует проверить все параметры метода. Если метод предназначен для вызова только известными сборками, необходимо сделать метод внутренним и применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> атрибут к сборке, содержащей метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, проверьте каждый аргумент `null`ссылки на.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если вы уверены, что параметр разыменования был проверен другим вызовом метода в функции.

## <a name="example"></a>Пример

В следующем примере показан метод, нарушающий правило, и метод, который удовлетворяет правилу.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Пример

Конструкторы копий, заполняющие поля или свойства, являющиеся ссылочными объектами, также могут нарушать правило CA1062. Нарушение возникает из-за того, что копируемый объект, передаваемый в конструктор `null` копирования`Nothing` , может быть (в Visual Basic). Чтобы устранить нарушение, используйте статический метод (Shared в Visual Basic), чтобы убедиться, что скопированный объект не имеет значение null.

В следующем `Person` примере класса `other` объект `Person` , который передается в конструктор копии, может иметь `null`значение.

```csharp
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

В следующем исправленном `Person` примере `other` объект, который передается в конструктор копии, сначала `PassThroughNonNull` проверяется на значение NULL в методе.

```csharp
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