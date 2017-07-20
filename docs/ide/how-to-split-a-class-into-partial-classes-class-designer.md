---
title: "Практическое руководство. Разделение класса на разделяемые классы (конструктор классов) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 9d74565f8e7e5b89e1716e9e2d88e2e18e077124
ms.contentlocale: ru-ru
ms.lasthandoff: 07/14/2017

---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Практическое руководство. Разделение класса в разделяемые классы (конструктор классов)
Объявление класса или структуры можно распределить по нескольким объявлениям с помощью ключевого слова `Partial` в Visual Basic или `partial` в Visual C#. Можно использовать столько частичных объявлений, сколько необходимо, как сразу в нескольких исходных файлах, так и только в одном. Однако все объявления должны находиться в одной сборке и одном пространстве имен.  
  
 Разделяемые классы могут быть очень полезны. Например, при работе над большими проектами разделение класса на несколько файлов позволяет работать с ним сразу нескольким разработчикам. При работе с кодом, созданным Visual Studio, класс можно изменить без повторного создания исходного файла. (Примеры кода, создаваемого Visual Studio: Windows Forms и программы-оболочки веб-служб.) Это позволяет составить код с использованием автоматически генерируемых классов, не изменяя файл, созданный Visual Studio.  
  
 Частичные методы бывают двух типов. Они называются объявлением и реализацией.  
  
 Конструктор классов поддерживает разделяемые классы и методы. Фигура типа в схеме классов относится к расположению отдельного объявления для разделяемого класса. Если разделяемый класс определен сразу в нескольких файлах, можно указать, какое расположение объявления будет использовать конструктор классов, настроив свойство **Расположение нового члена** в окне **Свойства**. В результате при двойном щелчке фигуры класса конструктор классов переходит в исходный файл, который содержит объявление класса, заданное свойством **Расположение нового члена**. При двойном щелчке разделяемого метода в фигуре класса конструктор классов переходит к объявлению разделяемого метода. Свойство **Имя файла** в окне **Свойства** также относится к расположению объявления. Для разделяемых классов в свойстве **Имя файла** перечисляются все файлы, содержащие код объявления и реализации для этого класса. При этом для разделяемых методов свойство **Имя файла** содержит только файл, содержащий объявление разделяемого метода.  
  
 Следующий пример разделяет определение класса `Employee` на два объявления, в каждом из которых определяется отдельная процедура. Два частичных определения в предыдущих примерах могут находиться в одном или двух исходных файлах.  
  
> [!NOTE]
>  Visual Basic использует определения разделяемых классов для отделения автоматически созданного кода от кода, созданного пользователем. Этот код разбивается на отдельные исходные файлы. Например, **конструктор форм Windows Forms** определяет разделяемые классы для элементов управления, таких как `Form`. Не следует изменять код, созданный в этих элементах управления.  
  
 Дополнительные сведения о разделяемых типах в Visual Basic см. в статье [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Пример  
 Чтобы разделить определение класса в Visual Basic, используйте ключевое слово `Partial`, как показано в следующем примере.  
  
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
  
## <a name="example"></a>Пример  
 Чтобы разделить определение класса в Visual C#, используйте ключевое слово `partial`, как показано в следующем примере.  
  
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
  
## <a name="see-also"></a>См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [Разделяемый (тип)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [Разделяемый (метод) (справочник по C#)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)
