---
title: Практическое руководство. Разделение класса в разделяемые классы (конструктор классов)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d0aa5b844b3743ab80c11971caa26340effe671
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Практическое руководство. Разделение класса на разделяемые классы (конструктор классов)

Объявление класса или структуры можно распределить по нескольким объявлениям с помощью ключевого слова `partial` (`Partial` в Visual Basic). Можно использовать неограниченное количество разделяемых объявлений.

Объявления могут находиться в одном или нескольких исходных файлах. Все объявления должны входить в одну сборку и одно пространство имен.

Разделяемые классы могут быть очень полезны. Например, при работе над большим проектом разделение класса на несколько файлов позволяет работать с ним сразу нескольким разработчикам. При работе с кодом, созданным Visual Studio, класс можно изменить без повторного создания исходного файла. (Примеры кода, создаваемого Visual Studio: Windows Forms и программы-оболочки веб-служб.) Это позволяет составить код с использованием автоматически генерируемых классов, не изменяя файл, созданный Visual Studio.

Частичные методы бывают двух типов. С C# и Visual Basic они называются объявлением и реализацией соответственно.

**Конструктор классов** поддерживает разделяемые классы и методы. Фигура типа в схеме классов относится к расположению отдельного объявления для разделяемого класса. Если разделяемый класс определен сразу в нескольких файлах, можно указать, какое расположение объявления будет использовать **конструктор классов**, настроив свойство **Расположение нового члена** в окне **Свойства**. В результате при двойном щелчке фигуры класса **конструктор классов переходит** в исходный файл, который содержит объявление класса, заданное свойством **Расположение нового члена**. При двойном щелчке разделяемого метода в фигуре класса **конструктор классов** переходит к объявлению разделяемого метода. Свойство **Имя файла** в окне **Свойства** также относится к расположению объявления. Для разделяемых классов в свойстве **Имя файла** перечисляются все файлы, содержащие код объявления и реализации для этого класса. При этом для разделяемых методов свойство **Имя файла** содержит только файл, содержащий объявление разделяемого метода.

Следующий пример разделяет определение класса `Employee` на два объявления, в каждом из которых определяется отдельная процедура. Два частичных определения в предыдущих примерах могут находиться в одном или двух исходных файлах.

> [!NOTE]
> Visual Basic использует определения разделяемых классов для отделения автоматически созданного кода от кода, созданного пользователем. Этот код разбивается на отдельные исходные файлы. Например, **конструктор форм Windows Forms** определяет разделяемые классы для элементов управления, таких как `Form`. Не следует изменять код, созданный в этих элементах управления.


Дополнительные сведения о разделяемых типах в Visual Basic см. в статье [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="visual-basic-example"></a>Пример в Visual Basic

Чтобы разделить определение класса в Visual Basic, используйте ключевое слово `Partial`, как показано в следующем примере.

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="c-example"></a>Пример в C#

Чтобы разделить определение класса в C#, используйте ключевое слово `partial`, как показано в следующем примере.

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

## <a name="see-also"></a>См. также

- [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (тип)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial (метод) (справочник по C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)