---
title: "CA1062: проверьте аргументы открытых методов | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: проверьте аргументы открытых методов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Видимый для внешнего кода методы выполняет разыменование одного из своих ссылочных аргументов, не проверяя его на равенство со значением `null` \(`Nothing` в Visual Basic\).  
  
## Описание правила  
 Все ссылочные аргументы, передаваемые в видимые для внешнего кода методы, должны проверяться на равенство значению `null`.  Если это возможно, при равенстве аргумента значению `null` следует вызывать исключение <xref:System.ArgumentNullException>.  
  
 Если метод может быть вызван из неизвестной сборки, поскольку был объявлен как открытый или защищенный, необходимо проверить все параметры метода.  Если метод сконструирован для вызова только известными сборками, следует сделать этот метод внутренним и применить атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> к сборке, содержащей этот метод.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, проверьте каждый ссылочный аргумент на равенство значению `null`.  
  
## Отключение предупреждений  
 Предупреждение из этого правила можно отключить, если вы уверены, что со снятой ссылкой параметр был проверен другим вызовом метода в функции.  
  
## Пример  
 В следующем примере показан метод, который нарушает данное правило, и метод, удовлетворяющий ему.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Пример  
 В [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] это правило не определяет ситуацию, когда параметры передаются другому методу, в котором производится такая проверка.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Пример  
 Конструкторы копирования, заполняющие поля или свойства, которые являются ссылочными объектами, также могут нарушать правило CA1062.  Нарушение возникает, если копируемый объект, который передается в конструктор копирования, может иметь значение `null` \(`Nothing` в Visual Basic\).  Чтобы устранить нарушение, используйте статический метод \(Shared в Visual Basic\), чтобы проверить, что скопированный объект не равен null.  
  
 В следующем примере класса `Person` объект `other`, который передается в конструктор копии `Person`, может быть равен `null`.  
  
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
  
## Пример  
 В следующем пересмотренном примере класса `Person` объект `other`, который передается в конструктор копии, сначала проверяется на равенство NULL в методе `PassThroughNonNull`.  
  
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