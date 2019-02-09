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
ms.openlocfilehash: 274b01a67974db08d9ec016a18ec115bcfac2452
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907975"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062. Проверьте аргументы или открытые методы

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Видимый извне метод разыменовывает одного из его аргументов ссылки без проверки, является ли этот аргумент `null` (`Nothing` в Visual Basic).

## <a name="rule-description"></a>Описание правила

Все ссылочные аргументы, передаваемые внешним видимым методам должны проверяться на `null`. При необходимости вызывать <xref:System.ArgumentNullException> когда аргумент является `null`.

Если метод может вызываться из неизвестных сборки, так как он объявлен как открытый или защищенный, следует проверить все параметры метода. Если метод должен вызываться только с помощью известных сборок, следует сделать метод внутренним и применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> атрибут к сборке, содержащий метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, проверьте каждый ссылочный аргумент от `null`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Если вы уверены, что со снятой ссылкой параметр был проверен другим вызовом метода в функцию можно отключить предупреждение из этого правила.

## <a name="example"></a>Пример

В примере показан метод, который нарушает правило и метод, соответствующий этому правилу.

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

Конструкторы копии, которые заполняют поля или свойства, которые будут ссылаться на объекты, также могут нарушать правило CA1062. Нарушение возникает, если копируемый объект, который передается в конструктор копии может быть `null` (`Nothing` в Visual Basic). Чтобы устранить нарушение, используйте статического метода (Shared в Visual Basic), чтобы проверить, что копируемый объект не равен null.

В следующем `Person` пример класса `other` объект, который передается `Person` конструктор копии может быть `null`.

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

В следующем примере пересмотра `Person` примере `other` объект, передаваемый в конструктор копирования сначала проверяется на null в `PassThroughNonNull` метод.

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