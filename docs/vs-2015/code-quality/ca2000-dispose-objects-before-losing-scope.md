---
title: CA2000. Ликвидировать объекты перед потерей области | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3456ec773b233da3ef2be1dfa7731460bdf6b44
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980119"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000. Ликвидируйте объекты перед потерей области
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Обратите внимание, что можно использовать `using` инструкции (`Using` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) для упаковки объектов, реализующих `IDisposable`. Объекты, которые упаковываются таким образом, автоматически удаляются при закрытии `using` блока.  
  
 Ниже приведены некоторые ситуации где с помощью инструкции недостаточно для защиты объектов IDisposable и может выдаваться CA2000 произойти.  
  
-   Возвращает высвобождаемый объект требует, что объект создается в блок try/finally вне using блока.  
  
-   Инициализация членов удаляемого объекта не следует выполнять в конструкторе с помощью инструкции.  
  
-   Вложенные конструкторы, которые защищены только одним обработчиком исключений. Например, примененная к объекту директива  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     вызывает CA2000, поскольку сбой в конструкции объекта StreamReader может привести в объект FileStream никогда не будет закрыт.  
  
-   Динамические объекты должны использовать теневой объект для реализации шаблона удаления объектов IDisposable.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Нельзя отключить предупреждения из этого правила, если не будет вызван метод на объекте, который вызывает `Dispose`, например <xref:System.IO.Stream.Close%2A>, или если метод, который вызвал предупреждение, возвращает объект IDisposable, который оборачивает ваш объект.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: Не удаляйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>Пример  
 При реализации метода, который возвращает удаляемый объект, используйте блок try/finally без блока catch, чтобы убедиться в том, что объект удален. С помощью блока try/finally, разрешить исключения вызывается в момент сбоя, и убедитесь, что удаление объекта.  
  
 В методе OpenPort1 Открытие ISerializable объект SerialPort или вызов метода SomeMethod может завершиться ошибкой. CA2000 предупреждение о реализации.  
  
 В методе OpenPort2 объявленных и имеет значение null, два объекта SerialPort:  
  
- `tempPort`, который используется для проверки успешного выполнения метода операции.  
  
- `port`, который используется для возвращаемого значения метода.  
  
  `tempPort` Создается и открывается в `try` блока, а также любые другие необходимые работа выполняется в том же `try` блока. В конце `try` блока, открытый порт назначается `port` объект, который будет возвращен и `tempPort` имеет значение `null`.  
  
  `finally` Блок проверяет значение параметра `tempPort`. Если он не равен null, произошел сбой операции в методе, и `tempPort` закрывается, чтобы убедиться в том, что все ресурсы будут освобождены. Объект возвращаемого порта будет содержать открытого объекта SerialPort, если операции метода выполнено успешно, или он будет иметь значение null, если операция завершилась ошибкой.  
  
  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>Пример  
 По умолчанию [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] у компилятора есть все арифметические операторы для переполнения. Таким образом, может вызывать любой арифметической операции Visual Basic <xref:System.OverflowException>. Это может привести к неожиданным нарушениям правил, например CA2000. Например следующая функция CreateReader1 приведет к нарушению CA2000 потому что компилятор Visual Basic создаются инструкции для добавления, которое может выдать исключение, которое приведет к тому, что StreamReader не будет удален проверки переполнения.  
  
 Чтобы устранить эту проблему, можно отключить создание проверок переполнения компилятором Visual Basic в проекте или можно изменить код, как показано в следующей функции CreateReader2.  
  
 Чтобы отключить проверку переполнения, щелкните правой кнопкой мыши имя проекта в обозревателе решений и нажмите кнопку **свойства**. Нажмите кнопку **компиляции**, нажмите кнопку **Дополнительные параметры компиляции**, а затем проверить **удалить проверки переполнения для целочисленных**.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable>   
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)