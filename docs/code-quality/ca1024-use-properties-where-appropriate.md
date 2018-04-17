---
title: 'CA1024: Используйте свойства, если это уместно | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bf44541c9eca3d2b8027ff1b5811caf0ba6824f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: используйте свойства, если это уместно
|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный метод имеет имя, которое начинается с `Get`, не принимает никаких параметров и возвращает значение, которое не является массивом.  
  
## <a name="rule-description"></a>Описание правила  
 В большинстве случаев свойства представляют данные, и методы выполнения действий. Доступ к свойствам как поля, что делает их проще использовать. Метод является хорошим кандидатом в качестве свойства, если присутствует одно из следующих условий:  
  
-   Не принимает аргументы и возвращает сведения о состоянии объекта.  
  
-   Принимает один аргумент для установки некоторой части состояния объекта.  
  
 Свойства должны представляться так, как если бы они были полей; Если метод не удается, он не должны изменяться со свойством. Методы работают лучше, чем свойства в следующих ситуациях:  
  
-   Этот метод выполняет длительную операцию. Метод ощутимо, чем время, когда необходимо задать или получить значение поля.  
  
-   Этот метод выполняет преобразование. Доступ к полю не возвращает преобразованную версию данных, который хранится.  
  
-   Метод Get оказывает видимое побочное действие. Получение значения поля не вызывает никаких побочных эффектов.  
  
-   Важен порядок выполнения. Установка значения поля не зависит от вхождения других операций.  
  
-   Вызов метода два раза подряд создает различные результаты.  
  
-   Метод является статическим, но возвращает объект, вызывающий объект может быть изменено. Получение значения поля не позволяет вызывающему объекту изменить данные, которые хранятся в поле.  
  
-   Метод возвращает массив.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените метод на свойство.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, если метод не отвечает по крайней мере один из перечисленных выше условий.  
  
## <a name="controlling-property-expansion-in-the-debugger"></a>Управление расширением свойств в отладчике  
 Одна из причин, программисты не использовать свойство — поскольку отладчик его автоматическое расширение не должен. Например свойство может включать выделения больших объектов или вызова P/Invoke, но он может фактически не иметь наблюдаемый побочных эффектов.  
  
 Отладчик может предотвратить автоматическое расширение свойств путем применения <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. В следующем примере показано этот атрибут применяется к экземпляру свойства.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```csharp  
  
      using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    publicclass TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере содержится несколько методов, должны быть преобразованы в свойства и следует не потому, что они не ведут себя как поля.  
  
 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]