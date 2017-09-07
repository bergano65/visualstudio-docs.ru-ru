---
title: "Настройка закодированного теста пользовательского интерфейса таким образом, чтобы во время воспроизведения он дожидался определенных событий | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: 24
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 40983f5c5c79f1555ea039df8d71c931fa633f24
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Настройка закодированного теста пользовательского интерфейса таким образом, чтобы во время воспроизведения он дожидался определенных событий
При воспроизведении закодированного теста ИП вы можете подождать возникновения определенных событий, например открытия окна, исчезновения строки хода выполнения и т. д. Чтобы сделать это, используйте соответствующий метод UITestControl.WaitForControlXXX(), как описано в следующей таблице. Пример закодированного теста пользовательского интерфейса, который ожидает включения элемента управления с помощью метода <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>, см. в разделе [Пошаговое руководство. Создание, изменение и обслуживание закодированного теста пользовательского интерфейса](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Требования**  
  
 Visual Studio Enterprise  
  
> [!TIP]
>  Вы также можете добавить задержки перед действиями с помощью редактора закодированных тестов пользовательского интерфейса. Дополнительные сведения см. в разделе [Практическое руководство. Вставка задержки перед действием пользовательского интерфейса с помощью редактора закодированных тестов пользовательского интерфейса](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **Методы UITestControl.WaitForControlXXX()**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Ожидает, когда этот элемент управления будет готов к приему ввода с помощью мыши и клавиатуры. Обработчик неявным образом вызывает этот API, чтобы все действия ожидали готовности элемента управления перед выполнением любой операции. Однако в некоторых особых случаях может потребоваться сделать явный вызов.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Ожидание элемента управления должно включаться, когда мастер выполняет определенную асинхронную проверку входных данных с помощью обращений к серверу. Например, метод может ожидать активации кнопки **Далее** мастера. Пример этого метода см. в разделе [Пошаговое руководство. Создание, изменение и обслуживание закодированного теста пользовательского интерфейса](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>  
  
 Ожидает появления элемента управления в пользовательском интерфейсе. Например, вы предполагаете, что после выполнения проверки параметров приложением появится диалоговое окно с ошибкой. Проверка может занимать разное время. Вы можете использовать этот метод для ожидания диалогового окна с ошибкой.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>  
  
 Ожидает исчезновения элемента управления из пользовательского интерфейса. Например, вы можете ожидать, когда исчезнет индикатор выполнения.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>  
  
 Ожидает, пока указанное свойство элемента управления не примет заданное значение. Например, вы можете ожидать, пока текст состояния не изменится на **Done**.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>  
  
 Ожидает, пока указанное свойство элемента управления не примет значение, противоположное заданному. Например, вы можете ожидать, когда поле ввода перестанет быть доступным только для чтения, то есть станет редактируемым.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>  
  
 Ожидает, пока указанный предикат не вернет значение `true`. Это может использоваться для составной операции ожидания (например, с условиями OR) в конкретном элементе управления. Например, вы можете ожидать, пока текст состояния не примет значение **Succeeded** или **Failed**, как показано в приведенном ниже коде.  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDone(UITestControl control)   
{   
    WinText statusText = control as WinText;   
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";   
}   
  
// In test method, wait till the method evaluates to true   
statusText.WaitForControlCondition(IsStatusDone);  
  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>  
  
 Все рассмотренные выше методы являются методами экземпляра UITestControl. Этот метод является статическим. Этот метод также ожидает, пока указанный предикат не примет значение `true`, но его можно использовать для составной операции ожидания (например, с условиями OR) в нескольких элементах управления. Например, вы можете ожидать, пока текст состояния не примет значение **Succeeded** или пока не появится сообщение об ошибке, как показано в приведенном ниже коде.  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDoneOrError(UITestControl[] controls)   
{   
    WinText statusText = controls[0] as WinText;   
    WinWindow errorDialog = controls[1] as WinWindow;   
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;   
}   
  
// In test method, wait till the method evaluates to true   
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);  
  
```  
  
 Все эти методы реализуют следующее поведение.  
  
 Эти методы возвращают значение true, если ожидание было успешно, или значение false, если ожидание завершилось неудачно.  
  
 Неявное время ожидания для операции ожидания задается свойством <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A>. По умолчанию значение этого свойства равно 60 000 миллисекундам (30 секундам).  
  
 Методы имеют перегрузку, чтобы принимать явное время ожидания в миллисекундах. Однако если операция ожидания приводит к неявному поиску элемента управления или если приложение занято, фактическое время ожидания может превышать заданное.  
  
 Предыдущие функции достаточно мощные и гибкие, чтобы удовлетворять почти все условия. Однако в случае, когда эти методы не удовлетворяют вашим потребностям и вам нужно включить в свой код метод <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> или <xref:System.Threading.Thread.Sleep%2A>, рекомендуется вместо API Thread.Sleep() использовать Playback.Wait(). Это объясняется следующими причинами.  
  
 Вы можете использовать свойство <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>, чтобы изменить длительность спящего режима. По умолчанию эта переменная имеет значение 1, но можно увеличить или уменьшить ее, чтобы изменить время ожидания для всего кода. Например, если тестирование выполняется в медленной сети или в другой ситуации с низкой производительностью, можно изменить эту переменную в одном месте (или даже в файле конфигурации) на 1,5, чтобы добавить дополнительные 50 % ожидания во всех местах.  
  
 Метод Playback.Wait() внутренним образом вызывает Thread.Sleep() (после вычисления, приведенного выше) в небольших блоках в цикле for при проверке операции cancel\break пользователя. Другими словами, метод Playback.Wait() позволяет отменить воспроизведение до окончания ожидания, в то время как спящий режим может не завершиться или вызвать исключение.  
  
> [!TIP]
>  Редактор закодированных тестов пользовательского интерфейса позволяет легко изменять закодированные тесты пользовательского интерфейса. С помощью редактора вы можете найти, просмотреть и изменить методы теста. Вы также можете редактировать действия ИП и связанные элементы управления на карте элементов управления ИП. Дополнительные сведения см. в разделе [Изменение закодированных тестов пользовательского интерфейса с помощью редактора закодированных тестов пользовательского интерфейса](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Руководство**  
  
 Дополнительные сведения см. в книге [Тестирование непрерывной доставки с использованием Visual Studio 2012, глава 5 "Автоматизация системных тестов"](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
## <a name="see-also"></a>См. также  
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)   
 [Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Пошаговое руководство. Создание, изменение и обслуживание закодированного теста пользовательского интерфейса](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Составляющие закодированного теста пользовательского интерфейса](../test/anatomy-of-a-coded-ui-test.md)   
 [Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Практическое руководство. Вставка задержки перед действием пользовательского интерфейса с помощью редактора закодированных тестов пользовательского интерфейса](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0)

