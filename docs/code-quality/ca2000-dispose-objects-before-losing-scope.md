---
title: 'CA2000: удалите объекты до того, как будет потеряна область действия'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 041cade3d1c65a40826920b94adf012aa9a4b021
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549874"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: удалите объекты до того, как будет потеряна область действия

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

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> в объекте, прежде чем все ссылки на него выходят за рамки.

 Обратите внимание, что можно использовать `using` инструкции (`Using` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) для упаковки объектов, реализующих `IDisposable`. Объекты, которые упаковываются таким образом, автоматически удаляются при закрытии `using` блока.

 Ниже приведены некоторые ситуации где с помощью инструкции недостаточно для защиты объектов IDisposable и может выдаваться CA2000 произойти.

- Возвращает высвобождаемый объект требует, что объект создается в блок try/finally вне using блока.

- Инициализация членов удаляемого объекта не следует выполнять в конструкторе с помощью инструкции.

- Вложенные конструкторы, которые защищены только одним обработчиком исключений. Например, примененная к объекту директива

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     вызывает CA2000, поскольку сбой в конструкции объекта StreamReader может привести в объект FileStream никогда не будет закрыт.

- Динамические объекты должны использовать теневой объект для реализации шаблона удаления объектов IDisposable.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Нельзя отключить предупреждения из этого правила, если не будет вызван метод на объекте, который вызывает `Dispose`, например <xref:System.IO.Stream.Close%2A>, или если метод, который вызвал предупреждение, возвращает объект IDisposable, который оборачивает ваш объект.

## <a name="related-rules"></a>Связанные правила
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: не удаляйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

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
 По умолчанию [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] у компилятора есть все арифметические операторы для переполнения. Таким образом, может вызывать любой арифметической операции Visual Basic <xref:System.OverflowException>. Это может привести к неожиданным нарушениям правил, например CA2000. Например следующая функция CreateReader1 приведет к нарушению CA2000 потому что компилятор Visual Basic создаются инструкции для добавления, которое может выдать исключение, которое приведет к тому, что StreamReader не будет удален проверки переполнения.

 Чтобы устранить эту проблему, можно отключить создание проверок переполнения компилятором Visual Basic в проекте или можно изменить код, как показано в следующей функции CreateReader2.

 Чтобы отключить проверку переполнения, щелкните правой кнопкой мыши имя проекта в обозревателе решений и нажмите кнопку **свойства**. Нажмите кнопку **компиляции**, нажмите кнопку **Дополнительные параметры компиляции**, а затем проверить **удалить проверки переполнения для целочисленных**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)