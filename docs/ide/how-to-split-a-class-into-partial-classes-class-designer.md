---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Объявление класса или структуры можно разделить между несколькими объявлениями, используя в Visual Basic ключевое слово `Partial` или в Visual C\# — `partial`.  Можно использовать столько разделяемых объявлений, сколько необходимо, и в стольких различных исходных файлах, в скольких требуется, или объявить все в одном исходном файле.  Однако все объявления должны находиться в одной и той же сборке и в одном и в том же пространстве имен.  
  
 Разделяемые классы полезны в нескольких случаях.  Например, если разработчик работает над большим проектом, то разделение класса в более чем один файл позволит работать над ним одновременно нескольким разработчикам.  При работе с кодом, создаваемым Visual Studio, можно изменить класс без повторного создания исходного файла.  \(Примеры кода, который создает Visual Studio, включают код программы\-оболочки Windows Forms и Web Service.\) Можно создать код, который использует автоматически создаваемые классы без изменения файлов, создаваемых Visual Studio.  
  
 Существует два вида разделяемых методов.  В Visual C\# и в Visual Basic они называются "объявление" и "реализация".  
  
 Конструктор классов поддерживает разделяемые классы и методы.  Фигура типа в схеме классов относится к одному расположению объявления для разделяемого класса.  Если разделяемый класс определен в нескольких файлах, то можно указать, какое расположение объявления конструктора класса будет использоваться настройками свойства **Расположение нового члена** в окне **Свойства**.  Т. е. при двойном щелчке мыши на фигуре класса конструктор классов перейдет к файлу исходного кода, содержащему объявление класса, указанное в свойстве **Расположение нового члена**.  При двойном щелчке мыши на разделяемом методе в фигуре класса конструктор классов перейдет к объявлению разделяемого метода.  Также к расположению объявления относится свойство **Имя файла** в окне **Свойства**.  Для разделяемых классов **Имя файла** перечисляет все файлы, содержащие объявление и реализацию кода для этого класса.  Однако для разделяемых методов **Имя файла** перечисляет только файл, содержащий объявление разделяемых методов.  
  
 В следующих примерах определение класса `Employee` разбивается на два объявления, каждое из которых определяет различную процедуру.  Два разделяемых определения в примерах могут находиться в одном исходном файле или в двух различных исходных файлах.  
  
> [!NOTE]
>  Visual Basic использует определения разделяемого класса, чтобы отделить код, созданный Visual Studio, от кода, созданного пользователем.  Код находится в отдельных исходных файлах.  Например, **Конструктор форм Windows Forms** определяет разделяемые классы для элементов управления, например `Form`.  Не следует изменять автоматически созданный код в этих элементах управления.  
  
 Дополнительные сведения о разделяемых типах в Visual Basic см. в разделе [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## Пример  
 Чтобы разделить определение класса в Visual Basic, используйте ключевое слово `Partial`, как показано в следующем примере:  
  
```vb#  
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
  
## Пример  
 Чтобы разделить определение класса в Visual C\#, используйте ключевое слово `partial`, как показано в следующем примере:  
  
```c#  
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
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial \(тип\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [разделяемый \(метод\) \(Справочник по C\#\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)