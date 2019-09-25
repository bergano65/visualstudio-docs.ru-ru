---
title: CA2000. Ликвидируйте объекты перед потерей области
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7a498a01741b86c16a52f790489dc8ce62aad06c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233232"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000. Ликвидируйте объекты перед потерей области

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Создается локальный объект <xref:System.IDisposable> типа, но объект не удаляется до тех пор, пока все ссылки на объект не выходят за пределы области.

## <a name="rule-description"></a>Описание правила

Если удаляемый объект не был явно удален до того, как все ссылки на него выходят за пределы области видимости, объект будет удален в неопределенное время, когда сборщик мусора выполняет метод завершения объекта. Так как может возникнуть исключительная ситуация, которая предотвратит выполнение метода завершения объекта, объект должен быть явно удален.

### <a name="special-cases"></a>Особые случаи

Правило CA2000 не срабатывает для локальных объектов следующих типов, даже если объект не удален:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Передача объекта одного из этих типов в конструктор, а затем присваивание его полю указывает на *передачу владения владельцем* вновь сформированного типа. То есть вновь сконструированный тип теперь отвечает за удаление объекта. Если код передает в конструктор объект одного из этих типов, нарушение правила CA2000 не происходит, даже если объект не удален, прежде чем все ссылки на него выходят из области.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> объект перед тем, как все ссылки на него выходят за пределы области.

Для создания оболочки объектов, реализующих <xref:System.IDisposable>, можно использовать [ `using` инструкцию](/dotnet/csharp/language-reference/keywords/using-statement) ([`Using`](/dotnet/visual-basic/language-reference/statements/using-statement) в Visual Basic). Объекты, обтекаемые таким способом, автоматически удаляются в конце `using` блока. Однако следующие ситуации не должны обрабатываться `using` оператором:

- Чтобы получить удаляемый объект, объект должен быть создан в `try/finally` блоке за пределами `using` блока.

- Не инициализируйте члены высвобождаемого объекта в конструкторе `using` инструкции.

- Если конструкторы, защищенные только одним обработчиком исключений, вложены в [ `using` инструкцию приобретения инструкции](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), ошибка внешнего конструктора может привести к тому, что объект, созданный вложенным конструктором, никогда не закрывается. В следующем примере сбой в <xref:System.IO.StreamReader> конструкторе может привести к тому, что <xref:System.IO.FileStream> объект никогда не закрывается. CA2000 помечает нарушение правила в этом случае.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Для реализации шаблона <xref:System.IDisposable> удаления объектов в динамических объектах следует использовать теневой объект.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение из этого правила, если:

- Вы вызвали метод для объекта, который вызывает `Dispose`, например<xref:System.IO.Stream.Close%2A>
- Метод, вызвавший предупреждение, возвращает <xref:System.IDisposable> объект, который создает оболочку для объекта
- Метод выделения не имеет владельца. то есть, ответственность за удаление объекта передается в другой объект или оболочку, которая создается в методе и возвращается вызывающему объекту.

## <a name="related-rules"></a>Связанные правила

- [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202 Не удалять объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Пример

При реализации метода, возвращающего удаляемый объект, используйте блок try/finally без блока catch, чтобы убедиться, что объект удален. С помощью блока try/finally можно разрешать возникновение исключений в точке сбоя и убедиться, что объект удален.

В методе OpenPort1 вызов для открытия объекта ISerializable SerialPort или вызова SomeMethod может завершиться ошибкой. В этой реализации возникает предупреждение CA2000.

В методе OpenPort2 объявляются два объекта SerialPort и устанавливается в значение NULL:

- `tempPort`, который используется для проверки успешности выполнения операций метода.

- `port`, который используется для возвращаемого значения метода.

Объект `tempPort` создается и открывается `try` в блоке, и любая другая требуемая работа выполняется в том же `try` блоке. В конце `try` блока открытый порт назначается `port` объекту, который `tempPort` будет возвращен, и для `null`объекта задается значение.

`finally` Блок проверяет `tempPort`значение. Если это значение не равно null, операция в методе завершилась неудачно и `tempPort` закрыта, чтобы убедиться, что все ресурсы освобождены. Возвращенный объект порта будет содержать открытый объект SerialPort, если операции метода завершились успешно, или значение null, если операция завершилась ошибкой.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If

   End Try

   Return port

End Function
```

## <a name="example"></a>Пример

По умолчанию компилятор Visual Basic имеет все арифметические операторы, которые проверяют переполнение. Таким образом, любая Visual Basic арифметическая операция может <xref:System.OverflowException>вызвать исключение. Это может привести к непредвиденным нарушениям правил, таких как CA2000. Например, следующая функция CreateReader1 выдаст нарушение CA2000, так как компилятор Visual Basic выдает инструкцию проверки переполнения для добавления, которая может вызвать исключение, которое привело бы к удалению StreamReader.

Чтобы устранить эту проблему, можно отключить эмиссию проверок переполнения компилятором Visual Basic в проекте или изменить код, как в следующей функции CreateReader2.

Чтобы отключить эмиссию проверок переполнения, щелкните правой кнопкой мыши имя проекта в обозреватель решений а затем выберите пункт **Свойства**. Нажмите кнопку **компилировать**, щелкните **Дополнительные параметры компиляции**, а затем установите флажок **Удалить проверки переполнения целых чисел**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)