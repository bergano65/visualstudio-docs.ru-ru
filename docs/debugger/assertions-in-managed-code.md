---
title: "Утверждения в управляемом коде | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 90e39956f777ddd79fad080d8bb6d13b30d4ccd0
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="assertions-in-managed-code"></a>Утверждения в управляемом коде
Оператор проверочного утверждения `Assert` проверяет выполнение условия, указанного в качестве аргумента для оператора `Assert`. Если условие выполняется, никаких действий не производится. Если же условие не выполняется, то утверждение выдает ошибку. При работе с отладочной сборкой выполнение программы приостанавливается.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Проверочные утверждения в пространстве имен System.Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Метод Debug.Assert](#BKMK_The_Debug_Assert_method)  
  
 [Побочные эффекты метода Debug.Assert](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Трассировки и отладки требования](#BKMK_Trace_and_Debug_Requirements)  
  
 [Аргументы методов Assert](#BKMK_Assert_arguments)  
  
 [Настройка поведения проверочных утверждений](#BKMK_Customizing_Assert_behavior)  
  
 [Использование проверочных утверждений в файлах конфигурации](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a>Проверочные утверждения в пространстве имен System.Diagnostics  
 В Visual Basic и Visual C# можно использовать метод `Assert` из класса <xref:System.Diagnostics.Debug> или из класса <xref:System.Diagnostics.Trace>, которые принадлежат пространству имен <xref:System.Diagnostics>. Методы класса <xref:System.Diagnostics.Debug> не включаются в окончательную версию (версию выпуска) программы, поэтому они не увеличивают ее размер и не уменьшают скорость ее выполнения.  
  
 C++ не поддерживает методы класса <xref:System.Diagnostics.Debug>. Того же эффекта можно добиться с помощью <xref:System.Diagnostics.Trace> класса с условной компиляции, такие как `#ifdef DEBUG`... `#endif`.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a>Метод Debug.Assert  
 Метод <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> можно свободно использовать для проверки условий, которые должны выполняться, если код программы написан правильно. Предположим, что имеется функция целочисленного деления. По правилам математики делитель не может быть равен нулю. Проверить выполнение этого условия в имеющейся функции можно при помощи утверждения:  
  
```VB  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```csharp  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 При запуске данного кода из отладчика оператор проверочного утверждения вычисляется, но в версию программы для выпуска он не войдет, а значит, не будет создавать дополнительной нагрузки.  
  
 Вот другой пример. Пусть имеется класс, описывающий текущий счет:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Прежде чем снять деньги со счета, необходимо удостовериться, что остаток на счете покрывает требуемую сумму. Для проверки остатка на счете можно написать проверочное утверждение:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Обратите внимание, что в версии для выпуска вызов метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> в коде будет отсутствовать. Это означает, что в версии для выпуска проверка остатка на счете производиться не будет. Чтобы решить эту проблему, следует поменять вызов метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> на вызов метода <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, который не исчезнет в версии для выпуска:  
  
 Вызовы <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> создают дополнительную нагрузку в версии выпуска, в отличие от вызовов <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a>Побочные эффекты метода Debug.Assert  
 При использовании метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> необходимо убедиться, что код внутри `Assert` не изменит результатов работы программы, если удалить `Assert`. В противном случае может быть создана ошибка, которая проявится только в версии программы для выпуска. Особая осторожность необходима в случае, если проверочное утверждение содержит вызовы функций или процедур, пример которых показан ниже:  
  
```VB  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 Такое использование метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> на первый взгляд может показаться безопасным, но предположим, например, что функция meas обновляет счетчик при каждом вызове. При сборке версии для выпуска вызов функции meas исчезнет, а значит, счетчик обновляться не будет. Это и есть пример функции, имеющей побочный эффект. Удаление вызова функции, имеющей побочные эффекты, может создать ошибку, которая проявится только в версии программы для выпуска. Чтобы избежать подобных проблем, не следует помещать вызовы функций в оператор метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>. Вместо этого следует использовать временную переменную:  
  
```VB  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```csharp  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 Даже при использовании метода <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> рекомендуется избегать размещения вызовов функций в операторе `Assert`. Такие вызовы, в принципе, безопасны, поскольку операторы <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> сохраняются в выпускной сборке. Однако, если взять за правило не использовать подобные конструкции, это снизит вероятность ошибки при использовании метода <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a>Трассировки и отладки требования  
 Если проект создается с помощью мастеров [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], символ TRACE определяется по умолчанию и в конфигурации выпуска, и в конфигурации отладки. Символ DEBUG определяется по умолчанию только в отладочной сборке.  
  
 Иначе для работы методов <xref:System.Diagnostics.Trace> требуется наличие одной из следующих строк в самом начале исходного файла:  
  
-   `#Const TRACE = True` — в Visual Basic  
  
-   `#define TRACE` — в Visual C# и C++  
  
 Либо, как вариант, построение программы должно выполняться с параметром TRACE:  
  
-   `/d:TRACE=True` — в Visual Basic  
  
-   `/d:TRACE` — в Visual C# и C++  
  
 Если методы Debug требуется использовать в выпускной сборке программы на языках C# или Visual Basic, необходимо определить символ DEBUG в конфигурации выпуска.  
  
 C++ не поддерживает методы класса <xref:System.Diagnostics.Debug>. Того же эффекта можно добиться с помощью <xref:System.Diagnostics.Trace> класса с условной компиляции, такие как `#ifdef DEBUG`... `#endif`. Можно определить эти символы в  **\<проект > страницы свойств** диалоговое окно. Дополнительные сведения см. в разделе [изменение параметров проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) или [изменение параметров проекта для конфигурации отладки C++ или C](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a>Аргументы методов Assert  
 Методы <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> и <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> принимают до трех аргументов. Первый аргумент является обязательным и задает условие, которое требуется проверить. При вызове метода <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> или <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> только с одним аргументом `Assert` метод проверяет условие и, если оно ложно, выведет содержимое стека вызовов для **вывода** окна. В следующем примере показаны методы <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> и <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:  
  
```VB  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 Второй и третий аргументы, если они присутствуют, должны иметь строковый формат. Если метод <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> или <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> вызывается с двумя или тремя аргументами, первым аргументом является условие. Метод проверяет условие и, если результат ложен, выводит вторую и третью строки. Ниже показаны примеры использования методов <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> и <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> с двумя аргументами:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 В следующем примере показаны методы <xref:System.Diagnostics.Debug.Assert%2A> и <xref:System.Diagnostics.Trace.Assert%2A>:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```csharp  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a>Настройка поведения проверочных утверждений  
 При запуске приложения в режиме пользовательского интерфейса `Assert` метод выводит **ложности** диалоговое окно «», если условие не выполняется. Действия, выполняемые при ошибке утверждения, определяются <xref:System.Diagnostics.Debug.Listeners%2A> или <xref:System.Diagnostics.Trace.Listeners%2A> свойства.  
  
 Можно настроить поведение при выводе отладочного сообщения путем добавления объекта <xref:System.Diagnostics.TraceListener> к коллекции `Listeners`, удаления <xref:System.Diagnostics.TraceListener> из коллекции `Listeners` или переопределения метода <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> существующего объекта `TraceListener` для изменения его поведения.  
  
 Например, можно переопределить <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> метода для записи в журнал событий вместо отображения **ложности** диалоговое окно.  
  
 Чтобы можно было настроить поведение программы таким образом, в программе должен быть прослушиватель, причем унаследованный от класса <xref:System.Diagnostics.TraceListener> и с переопределенным методом <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>.  
  
 Дополнительные сведения см. в разделе [прослушиватели трассировки](/dotnet/framework/debug-trace-profile/trace-listeners).  
  
 [Содержание раздела](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a>Использование проверочных утверждений в файлах конфигурации  
 Проверочные утверждения можно использовать в файле конфигурации программы, так же как и в коде. Дополнительные сведения см. в разделе <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> или <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Трассировка и инструментирование приложений](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)   
 [Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)