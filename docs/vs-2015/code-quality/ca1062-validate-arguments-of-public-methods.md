---
title: 'CA1062: Проверьте аргументы открытых методов | Документация Майкрософт'
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
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8fd4534c333dfe31801d13a99b6ee7b3f0c25e33
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592364"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: проверьте аргументы открытых методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1062: Проверьте аргументы открытых методов](https://docs.microsoft.com/visualstudio/code-quality/ca1062-validate-arguments-of-public-methods).

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

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Пример
 В [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], это правило не обнаруживает, что параметры передаются другому методу, который выполняет проверку.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Пример
 Конструкторы копии, которые заполняют поля или свойства, которые будут ссылаться на объекты, также могут нарушать правило CA1062. Нарушение возникает, если копируемый объект, который передается в конструктор копии может быть `null` (`Nothing` в Visual Basic). Чтобы устранить нарушение, используйте статического метода (Shared в Visual Basic), чтобы проверить, что копируемый объект не равен null.

 В следующем `Person` пример класса `other` объект, который передается `Person` конструктор копии может быть `null`.

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
 В следующем примере пересмотра `Person` примере `other` объект, передаваемый в конструктор копирования сначала проверяется на null в `PassThroughNonNull` метод.

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



