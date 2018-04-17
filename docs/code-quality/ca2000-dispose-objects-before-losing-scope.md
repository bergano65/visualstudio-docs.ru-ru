---
title: 'CA2000: Удалите объекты перед потерей области | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: d6771797128ba1f889f0639ea763a523353c8018
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: удалите объекты до того, как будет потеряна область действия
|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Категория|Microsoft.Reliability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Локальный объект <xref:System.IDisposable> создается тип, но прежде чем все ссылки на объект находятся вне области не удаляется объект.  
  
## <a name="rule-description"></a>Описание правила  
 Если удаляемый объект не высвобождается явно до все ссылки на него окажутся вне области, объект будет удален через некоторое неопределенное время, когда сборщик мусора запустит завершающий метод объекта. Так как может произойти исключительное событие, сделает невозможным метода завершения объекта Запуск объекта необходимо явно удалить вместо него.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, вызовите метод <xref:System.IDisposable.Dispose%2A> в объекте, прежде чем все ссылки на него окажутся вне области действия.  
  
 Обратите внимание, что можно использовать `using` инструкции (`Using` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) для упаковки объектов, реализующих `IDisposable`. Объекты, которые упаковываются таким образом, автоматически удаляются при закрытии `using` блока.  
  
 Ниже перечислены некоторые ситуации где с помощью оператора недостаточно для защиты объектов IDisposable и может выдаваться CA2000 возникать.  
  
-   Возвращение удаляемого объекта требует, что объект создается в блоке try/finally вне using блока.  
  
-   Инициализацию членов удаляемого объекта не следует выполнять в конструкторе с помощью инструкции.  
  
-   Вложенные конструкторы, которые защищены только одним обработчиком исключений. Например, примененная к объекту директива  
  
    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```
  
     в результате CA2000 возникает, поскольку сбой в конструкции объекта StreamReader может привести к объекту FileStream никогда не будет закрыт.  
  
-   Динамические объекты следует использовать теневой объект для реализации шаблона удаления объектов IDisposable.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Нельзя отключить предупреждения из этого правила, если не будет вызван метод на объекте, который вызывает `Dispose`, например <xref:System.IO.Stream.Close%2A>, или если метод, который вызвал предупреждение, возвращает объект IDisposable, который оборачивает ваш объект.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: не удаляйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>Пример  
 При реализации метода, возвращающего удаляемого объекта, используйте блок try/finally без блока catch важно убедиться, что объект удален. С помощью блока try/finally, исключений возникает в момент сбоя и убедитесь, что удаление объекта.  
  
 В методе OpenPort1 вызов открытия объекта ISerializable SerialPort или вызов SomeMethod может завершиться ошибкой. CA2000 предупреждение о реализации.  
  
 В методе OpenPort2 объявлен и задано значение null, два порта SerialPort объекта:  
  
-   `tempPort`, который используется для проверки успешного выполнения операций метода.  
  
-   `port`, который используется для возвращаемого значения метода.  
  
 `tempPort` Создан и открыт в `try` блока и любые другие необходимые работа выполняется в том же `try` блока. В конце `try` блок открытый порт назначается `port` объект, который будет возвращен и `tempPort` , присваивается значение `null`.  
  
 `finally` Блок проверяет значение свойства `tempPort`. Если не равно null, произошел сбой операции в методе, и `tempPort` закрыт, чтобы убедиться в том, что все ресурсы будут освобождены. Порт возвращаемый объект будет содержать открытого порта SerialPort объекта, если операции метода выполнено успешно, или он будет иметь значение null, если сбой операции.  

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
 По умолчанию [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] компилятор имеет все арифметические операторы на переполнение. Таким образом, может вызывать любой арифметической операции Visual Basic <xref:System.OverflowException>. Это может привести к неожиданным нарушениям правил, например CA2000. Например следующая функция CreateReader1 даст нарушение CA2000 так как компилятор Visual Basic выдающему инструкции проверки переполнения для добавления, которое может возникнуть исключение, которое приведет к тому, что StreamReader не удаляется.  
  
 Чтобы устранить эту проблему, можно отключить создание проверок переполнения компилятором Visual Basic в проекте или можно изменить код, как показано в следующей функции CreateReader2.  
  
 Чтобы отключить создание проверок переполнения, щелкните правой кнопкой мыши имя проекта в обозревателе решений и выберите **свойства**. Нажмите кнопку **компиляции**, нажмите кнопку **Дополнительные параметры компиляции**, а затем установите флажок **удалить проверки переполнения для целочисленных**.  
  
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>См. также  
 <xref:System.IDisposable>   
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)