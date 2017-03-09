---
title: "CA2000: удалите объекты до того, как будет потеряна область действия | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000: удалите объекты до того, как будет потеряна область действия
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Категория|Microsoft.Reliability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Создается локальный объект типа <xref:System.IDisposable>, который не удаляется до тех пор, пока все ссылки на объект не окажутся вне области действия.  
  
## Описание правила  
 Если освобождаемый объект не высвобождается явно до того, как все ссылки на него оказываются вне области имен, объект будет высвобожден в некоторый заранее не определенный момент, когда сборщик мусора запустит завершающий метод объекта.  Так как может возникнуть событие исключения, препятствующее выполнению метода завершения объекта, объект будет ликвидирован в явной форме.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, необходимо вызвать для объекта метод <xref:System.IDisposable.Dispose%2A>, прежде чем все ссылки на этот метод окажутся вне области действия.  
  
 Обратите внимание, что можно использовать выражение `using` \(`Using` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) для инкапсуляции объектов, реализующих `IDisposable`.  Объекты, упакованные таким образом, автоматически удаляются при закрытии блока `using`.  
  
 Следующие ситуации являются ситуациями, в которых использования оператора недостаточно для защиты объектов IDisposable и может выдаваться CA2000.  
  
-   Для возврата высвобождаемого объекта необходимо, чтобы объект создавался в блоке try\/finally вне блока using.  
  
-   Инициализацию членов удаляемого объекта не следует выполнять в конструкторе оператора using.  
  
-   Вложенные конструкторы, которые защищены только одним обработчиком исключений.  Например:  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     вызывает срабатывание CA2000, поскольку сбой в конструкции объекта StreamReader может привести к тому, что объект FileStream никогда не будет закрыт.  
  
-   Динамические объекты должны использовать теневой объект для реализации шаблона Dispose объектов IDisposable.  
  
## Отключение предупреждений  
 Нельзя отключить предупреждения из этого правила, если не будет вызван метод на объекте, который вызывает `Dispose`, например <xref:System.IO.Stream.Close%2A>, или если метод, который вызвал предупреждение, возвращает объект IDisposable, который оборачивает ваш объект.  
  
## Связанные правила  
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: не удаляйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## Пример  
 При реализации метода, возвращающего высвобождаемый объект, следует использовать блок try\/finally без блока catch, чтобы гарантировать, что объект удален.  Используя блок try\/finally, можно разрешить вызов исключений в момент сбоя и гарантировать удаление объекта.  
  
 В методе OpenPort1 вызов для открытия объекта ISerializable SerialPort или вызов SomeMethod может завершиться неудачей.  Предупреждение CA2000 вызывается для этой реализации.  
  
 В методе OpenPort2 два объекта SerialPort объявляются и задаются равными null:  
  
-   `tempPort`, который используется для проверки успешности выполнения операций метода.  
  
-   `port`, используемый для возвращаемого методом значения.  
  
 `tempPort` создан и открыт в блоке `try` и вся остальная необходимая работа выполняется в том же блоке `try`.  В конце блока `try` открытый порт назначается объекту `port`, который будет возвращен, а объекту `tempPort` устанавливается значение `null`.  
  
 Блок `finally` проверяет значение `tempPort`.  При значении, отличном от null, операцию в методе выполнить не удалось, и `tempPort` закрывается для гарантии, что все ресурсы будут освобождены.  Возвращаемый объект порта будет содержать открытый объект SerialPort, если операции метода выполнены успешно, или будет иметь значение NULL, если произошел сбой операции.  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## Пример  
 По умолчанию компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] имеет проверяет все арифметические операторы на переполнение.  Таким образом, любые арифметической операции в Visual Basic могут создавать <xref:System.OverflowException>.  Это могло привести к неожиданным нарушениям правил, например CA2000.  Например, следующая функция CreateReader1 создаст нарушение CA2000, так как компилятор Visual Basic выдает инструкции проверки переполнения для добавления, которое может создать исключение, приводящие к тому, что StreamReader не будет удален.  
  
 Для устранения этой проблемы можно отключить создание проверок переполнения компилятором Visual Basic в проекте или можно изменить код, как в следующей функции CreateReader2.  
  
 Чтобы отключить проверки переполнения, в обозревателе решений щелкните правой кнопкой мыши имя проекта и выберите **Свойства**.  Щелкните **Компилировать**, щелкните **Дополнительные параметры компиляции** и установите флажок **Удалить проверки переполнения для целочисленных значений**.  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## См. также  
 <xref:System.IDisposable>   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)