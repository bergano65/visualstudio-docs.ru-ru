---
title: 'CA2000: удаление объектов до потери области действия | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534775"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000. Ликвидируйте объекты перед потерей области
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Локальный объект <xref:System.IDisposable> типа создается, но объект не удаляется до тех пор, пока все ссылки на объект не выходят за пределы области.

## <a name="rule-description"></a>Описание правила
 Если удаляемый объект не был явно удален до того, как все ссылки на него выходят за пределы области видимости, объект будет удален в неопределенное время, когда сборщик мусора выполняет метод завершения объекта. Так как может возникнуть исключительная ситуация, которая предотвратит выполнение метода завершения объекта, объект должен быть явно удален.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> объект перед тем, как все ссылки на него выходят за пределы области.

 Обратите внимание, что можно использовать `using` оператор ( `Using` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) для заключения в оболочку объектов, реализующих `IDisposable` . Объекты, обтекаемые таким способом, автоматически удаляются в конце `using` блока.

 Ниже приведены ситуации, в которых инструкция using недостаточна для защиты объектов IDisposable и может привести к возникновению CA2000.

- Для возврата высвобождаемого объекта требуется, чтобы объект был создан в блоке try/finally за пределами блока using.

- Инициализация членов удаляемого объекта не должна выполняться в конструкторе оператора using.

- Вложенные конструкторы, защищенные только одним обработчиком исключений. Например, примененная к объекту директива

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     приводит к возникновению CA2000, поскольку сбой в построении объекта StreamReader может привести к тому, что объект FileStream никогда не закрывается.

- Для реализации шаблона удаления объектов IDisposable динамические объекты должны использовать теневой объект.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Нельзя отключить предупреждения из этого правила, если не будет вызван метод на объекте, который вызывает `Dispose`, например <xref:System.IO.Stream.Close%2A>, или если метод, который вызвал предупреждение, возвращает объект IDisposable, который оборачивает ваш объект.

## <a name="related-rules"></a>Связанные правила
 [CA2213. Следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202. Не ликвидируйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Пример
 При реализации метода, возвращающего удаляемый объект, используйте блок try/finally без блока catch, чтобы убедиться, что объект удален. С помощью блока try/finally можно разрешать возникновение исключений в точке сбоя и убедиться, что объект удален.

 В методе OpenPort1 вызов для открытия объекта ISerializable SerialPort или вызова SomeMethod может завершиться ошибкой. В этой реализации возникает предупреждение CA2000.

 В методе OpenPort2 объявляются два объекта SerialPort и устанавливается в значение NULL:

- `tempPort`, который используется для проверки успешности выполнения операций метода.

- `port`, который используется для возвращаемого значения метода.

  Объект `tempPort` создается и открывается в `try` блоке, и любая другая требуемая работа выполняется в том же `try` блоке. В конце `try` блока открытый порт назначается `port` объекту, который будет возвращен, и `tempPort` для объекта задается значение `null` .

  `finally`Блок проверяет значение `tempPort` . Если это значение не равно null, операция в методе завершилась неудачно и `tempPort` закрыта, чтобы убедиться, что все ресурсы освобождены. Возвращенный объект порта будет содержать открытый объект SerialPort, если операции метода завершились успешно, или значение null, если операция завершилась ошибкой.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Пример
 По умолчанию в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] компиляторе все арифметические операторы проверяют переполнение. Таким образом, любая Visual Basic арифметическая операция может вызвать исключение <xref:System.OverflowException> . Это может привести к непредвиденным нарушениям правил, таких как CA2000. Например, следующая функция CreateReader1 выдаст нарушение CA2000, так как компилятор Visual Basic выдает инструкцию проверки переполнения для добавления, которая может вызвать исключение, которое привело бы к удалению StreamReader.

 Чтобы устранить эту проблему, можно отключить эмиссию проверок переполнения компилятором Visual Basic в проекте или изменить код, как в следующей функции CreateReader2.

 Чтобы отключить эмиссию проверок переполнения, щелкните правой кнопкой мыши имя проекта в обозреватель решений а затем выберите пункт **Свойства**. Нажмите кнопку **компилировать**, щелкните **Дополнительные параметры компиляции**, а затем установите флажок **Удалить проверки переполнения целых чисел**.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>См. также
 <xref:System.IDisposable> [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)