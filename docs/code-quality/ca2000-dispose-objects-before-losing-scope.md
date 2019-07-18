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
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804977"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000. Ликвидируйте объекты перед потерей области

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Категория|Microsoft.Reliability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Локальный объект из <xref:System.IDisposable> тип создается, но объект не удален, прежде чем все ссылки на объект выходят за рамки.

## <a name="rule-description"></a>Описание правила

Если освобождаемый объект не высвобождается явно до все ссылки на него выходят за рамки, объект будет удален через некоторое неопределенное время, когда сборщик мусора запустит завершающий метод объекта. Так как может произойти исключительное событие, которое воспрепятствует финализатор объекта применялось, необходимо явно удалить объект вместо этого.

### <a name="special-cases"></a>Особые случаи

Даже если объект не удаляется правило CA2000 не срабатывают для локальных объектов следующих типов:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Указывает, передаче объекта одного из этих типов в конструктор и назначив его к полю *dispose передачи права владения* для вновь сконструированного типа. То есть вновь сконструированный тип теперь несет ответственность за освобождение объекта. Если код передает объект одного из этих типов в конструктор, не нарушение правила CA2000 происходит, даже если объект не удален перед все ссылки на него находятся вне области.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> в объекте, прежде чем все ссылки на него выходят за рамки.

Можно использовать [ `using` инструкции](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) в Visual Basic) для упаковки объектов, реализующих <xref:System.IDisposable>. Объекты, которые упаковываются таким образом, автоматически удаляются в конце `using` блока. Тем не менее, следующие ситуации не должны или не могут быть обработаны с `using` инструкции:

- Чтобы вернуть освобождаемый объект, объект должен создан в `try/finally` за пределами блока `using` блока.

- Не инициализировать членами удаляемого объекта в конструкторе класса `using` инструкции.

- Когда конструкторы, которые защищены только одним обработчиком исключений являются вложенными в [приобретения часть `using` инструкции](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), сбой в конструкторе внешнего может привести объект, созданный с помощью вложенных конструктора, никогда не закрывается. В следующем примере сбой в <xref:System.IO.StreamReader> может привести к конструктор <xref:System.IO.FileStream> объекта никогда не будет закрыт. CA2000 флаги таким образом, нарушение правила.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Динамические объекты должны использовать теневой объект для реализации шаблона удаления для <xref:System.IDisposable> объектов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключайте предупреждение из этого правила, если:

- Вызван метод на объекте, который вызывает `Dispose`, такие как <xref:System.IO.Stream.Close%2A>
- Метод, который вызвал предупреждение возвращает <xref:System.IDisposable> объект, который оборачивает ваш объект
- Метод выделения не имеет права владения dispose; то есть необходимо удалить объект передается другому объекту или программы-оболочки, который создается в методе и возвращается вызывающей стороне

## <a name="related-rules"></a>Связанные правила

- [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: Не удаляйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Пример

При реализации метода, который возвращает удаляемый объект, используйте блок try/finally без блока catch, чтобы убедиться в том, что объект удален. С помощью блока try/finally, разрешить исключения вызывается в момент сбоя, и убедитесь, что удаление объекта.

В методе OpenPort1 Открытие ISerializable объект SerialPort или вызов метода SomeMethod может завершиться ошибкой. CA2000 предупреждение о реализации.

В методе OpenPort2 объявленных и имеет значение null, два объекта SerialPort:

- `tempPort`, который используется для проверки успешного выполнения метода операции.

- `port`, который используется для возвращаемого значения метода.

`tempPort` Создается и открывается в `try` блока, а также любые другие необходимые работа выполняется в том же `try` блока. В конце `try` блока, открытый порт назначается `port` объект, который будет возвращен и `tempPort` имеет значение `null`.

`finally` Блок проверяет значение параметра `tempPort`. Если он не равен null, произошел сбой операции в методе, и `tempPort` закрывается, чтобы убедиться в том, что все ресурсы будут освобождены. Объект возвращаемого порта будет содержать открытого объекта SerialPort, если операции метода выполнено успешно, или он будет иметь значение null, если операция завершилась ошибкой.

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

По умолчанию компилятор Visual Basic имеет все арифметические операторы на переполнение. Таким образом, может вызывать любой арифметической операции Visual Basic <xref:System.OverflowException>. Это может привести к неожиданным нарушениям правил, например CA2000. Например следующая функция CreateReader1 приведет к нарушению CA2000 потому что компилятор Visual Basic создаются инструкции для добавления, которое может выдать исключение, которое приведет к тому, что StreamReader не будет удален проверки переполнения.

Чтобы устранить эту проблему, можно отключить создание проверок переполнения компилятором Visual Basic в проекте или можно изменить код, как показано в следующей функции CreateReader2.

Чтобы отключить проверку переполнения, щелкните правой кнопкой мыши имя проекта в обозревателе решений и нажмите кнопку **свойства**. Нажмите кнопку **компиляции**, нажмите кнопку **Дополнительные параметры компиляции**, а затем проверить **удалить проверки переполнения для целочисленных**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)