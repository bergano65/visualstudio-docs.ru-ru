---
title: "Разрешение вопросов, связанных с исключениями: System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException - класс"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.InvalidOperationException
Исключение <xref:System.InvalidOperationException?displayProperty=fullName> выдается, когда вызывается метод объекта в случае, если состояние объекта не поддерживает вызов метода. Исключение также выдается также в случае, когда метод пытается обработать пользовательский интерфейс из потока, не являющегося главным потоком или потоком пользовательского интерфейса.  
  
> [!IMPORTANT]
>  Так как исключения <xref:System.InvalidOperationException> могут выдаваться в различных ситуациях, очень важно прочесть и понять сообщение <xref:System.Exception.Message%2A>, отображаемое в помощнике по исключениям.  
  
##  <a name="BKMK_In_this_article"></a> Содержание этой статьи  
 [Метод, выполняемый в потоке, не связанном с пользовательским интерфейсом, обновляет пользовательский интерфейс](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [Оператор в блоке foreach (For Each в Visual Basic) изменяет коллекцию, в которой он выполняет итерации](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [Nullable&lt;T&gt;, имеющий значение null, приводится к T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [Метод System.Linq.Enumerable вызывается при пустой коллекции](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [Связанные статьи](#BKMK_Related_articles)  
  
 В примерах кода в этой статье показано, как некоторые общие исключения <xref:System.InvalidOperationException> могут появляться в вашем приложении. Способ обработки ошибок зависит от конкретной ситуации. Если исключение является неустранимым для функциональных возможностей приложения, то может потребоваться применение конструкции [try … catch](/dotnet/csharp/language-reference/keywords/exception-handling-statements) \([Try .. Catch](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) в Visual Basic\) для перехвата исключения и очистки состояния приложения перед выходом из него. Но, можно ожидать другие исключения <xref:System.InvalidOperationException> и избегать их. В приведенных примерах методов показаны некоторые такие способы.  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> Метод, выполняемый в потоке, не связанном с пользовательским интерфейсом, обновляет пользовательский интерфейс  
 [Вызов исключения InvalidOperationException с обновлением пользовательского интерфейса из потока без пользовательского интерфейса](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [Предотвращение исключения InvalidOperationException в потоках без пользовательского интерфейса](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 Большинство платформ приложений .NET GUI \(графический интерфейс пользователя\), например, Windows Forms и Windows Presentation Foundation \(WPF\) разрешают доступ к объектам графического интерфейса пользователя только из потока, который создает и управляет пользовательским интерфейсом \(поток **Main** или **UI**\). Исключение <xref:System.InvalidOperationException> возникает при попытке доступа к элементу пользовательского интерфейса из потока, который не является потоком пользовательского интерфейса.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> Вызов исключения InvalidOperationException с обновлением пользовательского интерфейса из потока без пользовательского интерфейса  
  
> [!NOTE]
>  В приведенном ниже примере для создания потоков без пользовательского интерфейса используется [Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md). Однако приведенные примеры также относятся ко всем [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md) .NET.  
  
 В этих примерах обработчик событий `ThreadsExampleBtn_Click` вызывает два раза метод `DoSomeWork`. Первый вызов метода \(`DoSomeWork(20);` запускается синхронно и выполняется успешно. Но второй вызов \(`Task.Run( () => { DoSomeWork(1000);});`\) выполняется в потоке в пределах [пула потоков](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx) приложения. Так как этот вызов пытается обновить интерфейс пользователя из потока без пользовательского интерфейса, то оператор создает исключение <xref:System.InvalidOperationException>  
  
 **Приложения WPF и Магазина**  
  
> [!NOTE]
>  В приложениях магазина Phone возникает исключение <xref:System.Exception>, а не более конкретное исключение <xref:System.InvalidOperationException>.  
  
 **Сообщения об исключениях:**  
  
|||  
|-|-|  
|Приложения WPF|Дополнительные сведения: вызывающий поток не может обратиться к этому объекту, так как им владеет другой поток.|  
|Приложения Магазина|Дополнительные сведения: приложение вызвало интерфейс, который был маршалирован для другого потока. \(Исключение из HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\)\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Приложения Windows Forms**  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: недопустимая операция в нескольких потоках: попытка доступа к элементу управления TextBox1 из потока, в котором он не был создан.  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Метод, выполняемый в потоке, не связанном с пользовательским интерфейсом, обновляет пользовательский интерфейс](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> Предотвращение исключения InvalidOperationException в потоках без пользовательского интерфейса  
 Платформы ИП Windows реализуют шаблон *диспетчера*, который содержит метод для проверки, выполняется ли вызов члена элемента пользовательского интерфейса в потоке ИП, а также другие методы для планирования вызова в потоке пользовательского интерфейса.  
  
 **Приложения WPF**  
  
 В приложениях WPF для выполнения делегата в потоке пользовательского интерфейса используйте один из методов <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName>. При необходимости, для определения, выполняется ли метод в потоке без пользовательского интерфейса, используйте метод <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName>.  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Приложения Windows Forms**  
  
 В приложениях Windows Form для выполнения делегата, который обновляет поток пользовательского интерфейса, используйте метод <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>. При необходимости, для определения, выполняется ли метод в потоке без пользовательского интерфейса, используйте свойство <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>.  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **Приложения Магазина**  
  
 В приложениях Магазина для выполнения делегата, который обновляет поток пользовательского интерфейса, используйте метод <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName>. При необходимости, для определения, выполняется ли метод в потоке без пользовательского интерфейса, используйте свойство <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A>.  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Метод, выполняемый в потоке, не связанном с пользовательским интерфейсом, обновляет пользовательский интерфейс](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> Оператор в блоке foreach \(For Each в Visual Basic\) изменяет коллекцию, в которой он выполняет итерации  
 [Вызов исключения InvalidOperationException с оператором foreach](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [Предотвращение исключения InvalidOperationException в циклах](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 Оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) \([For Each](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) в Visual Basic\) повторяет группу вложенных операторов для каждого элемента массива или коллекции, которая реализует интерфейс <xref:System.Collections.IEnumerable?displayProperty=fullName> или <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>. Оператор `foreach` используется для итерации по коллекции для чтения и изменения элементов, но не может применяться для добавления или удаления элементов из коллекции. Исключение <xref:System.InvalidOperationException> появляется в случае добавления или удаления элементов из исходной коллекции в операторе foreach.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> Вызов исключения InvalidOperationException с оператором foreach  
 В этом примере появляется исключение <xref:System.InvalidOperationException>, когда оператор `numList.Add(5);` пытается изменить список в блоке foreach.  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: коллекция была изменена; невозможно выполнить операцию перечисления.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Оператор в блоке foreach (For Each в Visual Basic) изменяет коллекцию, в которой он выполняет итерации](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> Предотвращение исключения InvalidOperationException в циклах  
  
> [!IMPORTANT]
>  Добавление и удаление элементов из списка в ходе выполнения итераций в коллекции может создать непредвиденные и трудно предсказуемые побочные эффекты. Если возможно, переместите операцию за пределы итерации.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 Если вам необходимо добавить или удалить элементы из списка в ходе выполнения итерации в коллекции, используйте цикл [for](/dotnet/csharp/language-reference/keywords/for) \([For](/dotnet/visual-basic/language-reference/statements/for-next-statement) в Visual Basic\):  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Оператор в блоке foreach (For Each в Visual Basic) изменяет коллекцию, в которой он выполняет итерации](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> Nullable\<T\>, имеющий значение null, приводится к T  
 [Вызов исключения InvalidOperationException с недопустимым приведением](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [Предотвращение исключения InvalidOperationException из плохого приведения](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 Если вы приводите структуру <xref:System.Nullable%601>, которая имеет значение `null` \(`Nothing` в Visual Basic\) к ее базовому типу, то создается исключение <xref:System.InvalidOperationException>.  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> Вызов исключения InvalidOperationException с недопустимым приведением  
 В этом методе создается исключение <xref:System.InvalidOperationException>, когда метод Select приводит элемент null в dbQueryResults к типу int.  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: объект, допускающий значение null, должен иметь значение.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Nullable&lt;T&gt;, имеющий значение null, приводится к T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> Предотвращение исключения InvalidOperationException из плохого приведения  
 Для предотвращения исключения <xref:System.InvalidOperationException>:  
  
-   Используйте свойство <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> для выбора только тех элементов, которые не являются нулевыми.  
  
-   Используйте один из перегруженных методов <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> для назначения элементу null значения по умолчанию.  
  
 **Пример значения Nullable\<T\>.HasValue**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Пример значения Nullable\<T\>.GetValueOrDefault**  
  
 В этом примере метод <xref:System.Nullable%601.GetValueOrDefault%28%600%29> используется для задания значения по умолчанию, которое находится за пределами ожидаемых значений, возвращаемых операцией `dbQueryResults`.  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Nullable&lt;T&gt;, имеющий значение null, приводится к T](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> Метод System.Linq.Enumerable вызывается при пустой коллекции  
 Методы <xref:System.Linq.Enumerable>, <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.First%2A>, <xref:System.Linq.Enumerable.Single%2A> и <xref:System.Linq.Enumerable.SingleOrDefault%2A> выполняют операции над последовательностью и возвращают один результат.  
  
 Некоторые перегрузки этих методов создают исключение <xref:System.InvalidOperationException>, если последовательность является пустой \(другие перегрузки возвращают значение `null` \(`Nothing` в Visual Basic\).<xref:System.Linq.Enumerable.SingleOrDefault%2A> также создает исключение <xref:System.InvalidOperationException>, если последовательность содержит несколько элементов.  
  
> [!TIP]
>  Большинство методов <xref:System.Linq.Enumerable>, рассмотренных в этом разделе, являются перегруженными. Убедитесь, что вы понимаете поведение выбираемой перегрузки.  
  
 **Сообщения об исключениях:**  
  
 [Методы Aggregate, Average, Last, Max и Min](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [Методы First и FirstOrDefault](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Методы Single и SingleOrDefault](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Методы Aggregate, Average, Last, Max и Min  
  
-   Дополнительные сведения: последовательность не содержит элементов  
  
 **Вызов исключения InvalidOperationException с помощью метода Average**  
  
 В этом примере следующий метод создает исключение <xref:System.InvalidOperationException> при вызове метода <xref:System.Linq.Enumerable.Average%2A>, так как выражение Linq возвращает последовательность, не содержащую элементы, которые больше 4.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 При использовании одного из этих методов без проверки на пустую последовательность неявно предполагается, что последовательность не является пустой, и что пустая последовательностью не ожидается. Перехват или создание исключения можно использовать, если вы предполагаете, что последовательность не будет пустой.  
  
 **Предупреждение исключения InvalidOperationException, вызываемого пустой последовательностью**  
  
 Для проверки, является ли последовательность пустой, используйте один из методов <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName>.  
  
> [!TIP]
>  Применение выражения <xref:System.Linq.Enumerable.Any%2A> может повышать производительность проверки, если последовательность усреднения может содержать большое количество элементов, или если операцию, которая создает последовательность, является дорогостоящей.  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Метод System.Linq.Enumerable вызывается при пустой коллекции](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> Методы First и FirstOrDefault  
 Выражение <xref:System.Linq.Enumerable.First%2A> возвращает первый элемент последовательности или создает исключение <xref:System.InvalidOperationException>, если последовательность является пустой.  Для возвращения заданного значения или значения по умолчанию вместо создания исключения можно вызывать метод <xref:System.Linq.Enumerable.FirstOrDefault%2A> вместо метода <xref:System.Linq.Enumerable.First%2A>.  
  
> [!NOTE]
>  На платформе .NET Framework типы имеют концепцию значений по умолчанию. Например, для любого ссылочного типа значением по умолчанию является null, а значением по умолчанию для целочисленного типа является нуль. См. раздел [Таблица значений по умолчанию](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Вызов исключения InvalidOperationException с помощью метода First**  
  
 <xref:System.Linq.Enumerable.First%2A> — это метод оптимизации, возвращающий первый элемент последовательности, который удовлетворяет заданному условию. Если элемент, удовлетворяющий условию, не будет найден, то методы создают исключение <xref:System.InvalidOperationException>.  
  
 В этом примере метод `First` создает исключение, так как `dbQueryResults` не содержит элемент, который больше, чем 4.  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: последовательность не содержит совпадающие элементы  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **Предотвращение исключения с помощью FirstOrDefault**  
  
 Для проверки, что последовательность <xref:System.Linq.Enumerable.FirstOrDefault%2A> содержит хотя бы один элемент, можно использовать один из методов <xref:System.Linq.Enumerable.First%2A> вместо метода `firstNum`. Если запрос не находит элемент, удовлетворяющий условию, он возвращает заданное значение или значение по умолчанию. Чтобы определить, обнаружены ли какие\-либо элементы, можно проверить возвращаемое значение.  
  
> [!NOTE]
>  Процедура реализации метода <xref:System.Linq.Enumerable.FirstOrDefault%2A> может быть более сложной, если значением по умолчанию для типа является допустимый элемент в последовательности.  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Метод System.Linq.Enumerable вызывается при пустой коллекции](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Методы Single и SingleOrDefault  
 Методы <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> возвращают единственный элемент последовательности или единственный элемент последовательности, который удовлетворяет заданному тесту.  
  
 Если в последовательности элементы отсутствуют, или имеется несколько элементов, то метод создает исключение <xref:System.InvalidOperationException>.  
  
 Для возвращения заданного значения или значения по умолчанию, вместо создания исключения, если последовательность не содержит элементов, можно использовать метод <xref:System.Linq.Enumerable.SingleOrDefault%2A>. Однако метод <xref:System.Linq.Enumerable.SingleOrDefault%2A> по\-прежнему создает исключение <xref:System.InvalidOperationException>, если последовательность содержит несколько элементов, удовлетворяющего предикату выбора.  
  
> [!NOTE]
>  На платформе .NET Framework типы имеют концепцию значений по умолчанию. Например, для любого ссылочного типа значением по умолчанию является null, а значением по умолчанию для целочисленного типа является нуль. См. раздел [Таблица значений по умолчанию](/dotnet/csharp/language-reference/keywords/default-values-table).  
  
 **Вызов исключений InvalidOperationException с помощью метода Single**  
  
 В этом примере метод `singleObject` создает исключение <xref:System.InvalidOperationException>, так как `dbQueryResults` не содержит элемент, который больше 4.  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: последовательность не содержит совпадающие элементы  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **Вызов исключений InvalidOperationException с помощью метода Single или SingleOrDefault**  
  
 В этом примере метод `singleObject` создает исключение <xref:System.InvalidOperationException>, так как `dbQueryResults` содержит несколько элементов, которые больше 2.  
  
 **Сообщение об исключении:**  
  
-   Дополнительные сведения: последовательность содержит несколько совпадающих элементов  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **Предотвращение исключений InvalidOperationException с помощью метода Single**  
  
 Методы <xref:System.Linq.Enumerable.Single%2A> и <xref:System.Linq.Enumerable.SingleOrDefault%2A> также можно использовать для обозначения свои намерений.<xref:System.Linq.Enumerable.Single%2A> строго подразумевает, что из условия предполагается возвращение только одного результата.<xref:System.Linq.Enumerable.SingleOrDefault%2A> объявляет, что ожидается один результат или нулевые результаты, но не более того. При несоблюдении этих условий может происходить создание или перехват исключения <xref:System.InvalidOperationException>. Тем не менее, если предполагается, что недопустимые условия будут происходить с некоторой частотой, для формирования результатов следует использовать другие методы <xref:System.Linq.Enumerable>, например, <xref:System.Linq.Enumerable.First%2A> или <xref:System.Linq.Enumerable.Where%2A>.  
  
 Во время разработки для проверки своих предположений можно использовать один из методов <xref:System.Diagnostics.Debug.Assert%2A>. В этом примере выделенный код вызывает останов отладчика и отображение диалогового окна утверждения во время разработки. Если результаты являются недопустимыми, утверждение удаляется из кода выпуска, и будет создаваться любой метод <xref:System.Linq.Enumerable.Single%2A>.  
  
> [!NOTE]
>  Если применяется метод <xref:System.Linq.Enumerable.Take%2A>, а для его параметра `count` установлено значение 2, то возвращаемая последовательность будет ограничена, по крайней мере, двумя элементами. Эта последовательность включает в себя все случаи, которые необходимо проверить \(0, 1 и свыше 1 элемента\), и может повысить производительность проверки, когда последовательность может содержать большое количество элементов, или если операция, создающая последовательность, является дорогостоящей.  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 Если необходимо избегать исключения, но по\-прежнему обрабатывать недопустимые состояния в коде выпуска, то способ, описанный выше, можно изменить. В этом примере метод реагирует на количество элементов, возвращаемых методом `moreThan2`, в операторе switch.  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [Метод System.Linq.Enumerable вызывается при пустой коллекции](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> Связанные статьи  
 [Правила разработки исключений \(рекомендации по разработке .NET Framework\)](http://msdn.microsoft.com/library/ms229014)  
  
 [Обработка и создание исключений \(основные сведения о приложениях .NET Framework\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [Практическое руководство. Получение уведомлений о первичном исключении \(руководство по разработке для .NET Framework\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [Практическое руководство. Обработка исключений в запросе PLINQ \(руководство по разработке для .NET Framework\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [Исключения в управляемых потоках \(руководство по разработке для .NET Framework\)](http://msdn.microsoft.com/library/ms228965)  
  
 [Исключения и обработка исключений \(Руководство по программированию в C\#\)](http://msdn.microsoft.com/library/ms173160)  
  
 [Операторы обработки исключений \(Справочник по C\#\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Оператор Try... Catch... Finally \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [Обработка исключений \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [Исключения в C\+\+\/CLI](http://msdn.microsoft.com/library/Hh875008)  
  
 [Обработка исключений \(библиотека параллельных задач\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [Обработка исключений \(отладка\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [Пошаговое руководство. Обработка исключения параллельности \(доступ к данным в Visual Studio\)](http://msdn.microsoft.com/library/ms171936)  
  
 [Практическое руководство. Обработка ошибок и исключений, происходящих при связывании элементов управления с данными \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [Обработка исключений в сетевых приложениях \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![К началу](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Содержание этой статьи](#BKMK_In_this_article)