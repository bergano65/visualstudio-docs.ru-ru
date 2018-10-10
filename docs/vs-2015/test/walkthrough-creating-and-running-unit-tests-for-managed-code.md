---
title: Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a0bc6ab5854d0db9fc5bae7c642b804bc5af27a
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881115"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: Создание и запуск модульных тестов для управляемого кода](https://docs.microsoft.com/visualstudio/test/walkthrough-creating-and-running-unit-tests-for-managed-code).  
  
В этом пошаговом руководстве приводится подробное описание процесса создания, запуска и настройки набора модульных тестов с помощью платформы модульных тестов Microsoft для управляемого кода и обозревателя тестов Visual Studio. В руководстве производится создание проекта C#, находящегося в стадии разработки, создание тестов для проверки его кода, запуск тестов и изучение результатов. После этого производится изменение кода проекта и повторный запуск тестов.  
  
 В этом разделе содержатся следующие подразделы.  
  
 [Подготовка к выполнению пошагового руководства](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Создание проекта модульного теста](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Создание тестового класса](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
-   [Требования к тестовому классу](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
 [Создание первого тестового метода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
-   [Требования к методу теста](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
 [Сборка и запуск теста](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
 [Исправление кода и повторный запуск тестов](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
 [Использование модульных тестов для улучшения кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  В этом пошаговом руководстве используется платформа модульных тестов Microsoft для управляемого кода. Обозреватель тестов также может запускать тесты c платформ модульных тестов стороннего производителя, которые имеют адаптеры для обозревателя тестов. Дополнительные сведения см. в разделе [Установка платформ модульного тестирования сторонних поставщиков](../test/install-third-party-unit-test-frameworks.md).  
  
> [!NOTE]
>  Сведения о запуске тестов из командной строки см. в разделе [Пошаговое руководство. Использование служебной программы для тестирования с интерфейсом командной строки](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Проект "Банк". См. раздел [Пример проекта для создания модульных тестов](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> Подготовка к выполнению пошагового руководства  
  
1.  Запустите Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать** , а затем команду **Проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
3.  В области **Установленные шаблоны**выберите шаблон **Visual C#**.  
  
4.  В списке типов приложения выберите пункт **Библиотека классов**.  
  
5.  В поле **Имя** введите `Bank` , а затем команду **ОК**.  
  
    > [!NOTE]
    >  Если имя "Bank" уже существует, выберите для проекта другое имя.  
  
     Будет создан новый проект Bank. Этот проект отобразится в обозревателе решений, а его файл Class1.cs откроется в редакторе кода.  
  
    > [!NOTE]
    >  Если файл Class1.cs не откроется в редакторе кода, дважды щелкните Class1.cs в обозревателе решений, чтобы открыть этот файл.  
  
6.  Скопируйте исходный код из раздела [Пример проекта для создания модульных тестов](../test/sample-project-for-creating-unit-tests.md).  
  
7.  Замените исходное содержимое файла Class1.cs кодом из раздела [Пример проекта для создания модульных тестов](../test/sample-project-for-creating-unit-tests.md).  
  
8.  Сохранение файла как BankAccount.cs  
  
9. В меню **Сборка** выберите **Собрать решение**.  
  
 Будет создан проект с именем "Bank". Он содержит исходный код, подлежащий тестированию, и средства для его тестирования. Пространство имен проекта "Bank", **BankAccountNS**, содержит открытый класс **BankAccount**, методы которого будут тестироваться в приведенных ниже процедурах.  
  
 В данном кратком руководстве рассматривается метод `Debit` . Метод Debit вызывается после снятия денег со счета и содержит следующий код:  
  
```csharp  
// method under test  
public void Debit(double amount)  
{  
    if(amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    m_balance += amount;  
}  
  
```  
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Создание проекта модульного теста  
 **Предварительное требование**: необходимо выполнить действия, приведенные в подразделе [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Создание проекта модульного теста  
  
1.  В меню **Файл** последовательно щелкните **Добавить**и **Новый проект...**.  
  
2.  В диалоговом окне "Новый проект" разверните узлы **Установленные**и **Visual C#** и выберите **Тест**.  
  
3.  В списке шаблонов выберите **Проект модульного теста**.  
  
4.  В поле **Имя** введите BankTest и нажмите кнопку **ОК**.  
  
     Проект **BankTests** добавляется в решение **Банк**.  
  
5.  В проекте **BankTests** добавьте ссылку на решение **Банк** .  
  
     В области "Обозреватель решений" выберите **Ссылки** в проекте **BankTests** , а затем выберите **Добавить ссылку...** из контекстного меню.  
  
6.  В диалоговом окне "Диспетчер ссылок" разверните **Решение** и проверьте элемент **Банк** .  
  
##  <a name="BKMK_Create_the_test_class"></a> Создание тестового класса  
 Тестовый класс нужен для проверки класса `BankAccount` . Можно использовать UnitTest1.cs, созданный в шаблоне проекта, но лучше дать файлу и классу более описательные имена. Можно сделать это за один шаг, переименовав файл в обозревателе решений.  
  
 **Переименование файла класса**  
  
 В обозревателе решений выберите файл UnitTest1.cs в проекте BankTests. В контекстном меню выберите команду **Переименовать**, а затем переименуйте файл в BankAccountTests.cs. Выберите **Да** в диалоговом окне, предлагающем переименовать все ссылки на элемент кода "UnitTest1" в проекте. Этот шаг изменяет имя класса на `BankAccountTest`.  
  
 Файл BankAccountTests.cs теперь содержит следующий код:  
  
```csharp  
// unit test code  
using System;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
namespace BankTests  
{  
    [TestClass]  
    public class BankAccountTests  
    {  
        [TestMethod]  
        public void TestMethod1()  
        {  
        }  
    }  
}  
```  
  
 **Добавление оператора using в тестируемый проект**  
  
 Можно также добавить оператор using в класс, чтобы тестируемый проект можно было вызывать без использования полных имен. Вверху файла класса добавьте:  
  
```csharp  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Требования к тестовому классу  
 Минимальные требования к тестовому классу следующие:  
  
-   Атрибут `[TestClass]` является обязательным для платформы модульных тестов Microsoft для управляемого кода в любом классе, содержащем методы модульных тестов, которые необходимо выполнить в обозревателе тестов.  
  
-   Каждый метод теста, предназначенный для запуска в обозревателе тестов, должен иметь атрибут `[TestMethod]`.  
  
 Можно иметь другие классы в проекте модульного теста, которые не содержат атрибута `[TestClass]` , а также иметь другие методы в тестовых классах, у которых атрибут — `[TestMethod]` . Можно использовать эти другие классы и методы в методах теста.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> Создание первого тестового метода  
 В этой процедуре мы напишем методы модульного теста для проверки поведения метода `Debit` класса `BankAccount` . Этот метод приведен выше.  
  
 Путем анализа тестируемого метода мы определили, что необходимо проверить по меньшей мере три поведения.  
  
1.  Метод создает исключение [ArgumentOutOfRangeException] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->) Если сумма по дебету превышает баланс.  
  
2.  Он также создает исключение `ArgumentOutOfRangeException` , если сумма по дебету меньше нуля.  
  
3.  Если проверка пунктов 1.) и 2.) проходит успешно, то метод вычитает сумму из баланса счета.  
  
 В первом тесте проверим, снимается ли со счета нужная сумма при допустимом размере кредита (со значением меньшим, чем баланс счета, и большим, чем ноль).  
  
#### <a name="to-create-a-test-method"></a>Создание метода теста  
  
1.  Добавьте инструкцию using `BankAccountNS;` в файл BankAccountTests.cs.  
  
2.  Добавьте следующий метод в этот класс `BankAccountTests` :  
  
    ```csharp  
    // unit test code  
    [TestMethod]  
    public void Debit_WithValidAmount_UpdatesBalance()  
    {  
        // arrange  
        double beginningBalance = 11.99;  
        double debitAmount = 4.55;  
        double expected = 7.44;  
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
        // act  
        account.Debit(debitAmount);  
  
        // assert  
        double actual = account.Balance;  
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
    }  
    ```  
  
 Этот метод достаточно прост. Мы создаем новый объект `BankAccount` с начальным балансом, а затем снимаем допустимое значение. Используем платформу модульных тестов Microsoft для метода <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> управляемого кода, чтобы проверить соответствие конечного баланса ожидаемому.  
  
###  <a name="BKMK_Test_method_requirements"></a> Требования к методу теста  
 Метод теста должен удовлетворять следующим требованиям:  
  
-   Метод должен быть отмечен атрибутом `[TestMethod]` .  
  
-   Метод должен вернуть `void`.  
  
-   Метод не должен иметь параметров.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Сборка и запуск теста  
  
#### <a name="to-build-and-run-the-test"></a>Сборка и запуск теста  
  
1.  В меню **Построение** выберите **Построить решение**.  
  
     Если ошибок нет, появится окно UnitTestExplorer с элементом **Debit_WithValidAmount_UpdatesBalance** в группе **Незапускавшиеся тесты** . Если обозреватель тестов не откроется после успешной сборки, выберите в меню пункт **Тест** , щелкните **Windows**, а затем —  **Обозреватель тестов**.  
  
2.  Выберите **Запустить все** , чтобы выполнить тест. Во время выполнения теста в верхней части окна отображается анимированная строка состояния. По завершении тестового запуска строка состояния становится зеленой, если все методы теста успешно пройдены, или красной, если какие-либо из тестов не пройдены.  
  
3.  В данном случае тест пройден не будет. Метод теста будет перемещен в группу **Непройденные тесты** . Выберите этот метод в обозревателе тестов для просмотра сведений в нижней части окна.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Исправление кода и повторный запуск тестов  
 **Анализ результатов теста**  
  
 Результат теста содержит сообщение, описывающее возникшую ошибку. Для метода `AreEquals` сообщение отражает ожидаемый результат (параметр **Expected\<*XXX*>**) и фактически полученный (параметр **Actual\<*YYY*>**). Ожидалось, что баланс уменьшится относительно начального баланса, но вместо этого произошло его увеличение на сумму списания.  
  
 Повторная проверка кода "Дебит" показывает, что модульный тест позволил успешно найти ошибку. Сумма списания добавляется на баланс счета, а не вычитается.  
  
 **Исправление ошибки**  
  
 Для исправления ошибки просто замените строку  
  
```csharp  
m_balance += amount;  
```  
  
 на  
  
```csharp  
m_balance -= amount;  
```  
  
 **Повторный запуск теста**  
  
 В обозревателе тестов выберите **Запустить все** , чтобы запустить тест повторно. Красно-зеленая строка состояния станет зеленой, и тест будет перемещен в группу **Пройденные тесты** .  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Использование модульных тестов для улучшения кода  
 В этом разделе рассматривается, как последовательный процесс анализа, разработки модульных тестов и рефакторинга может помочь сделать рабочий код более надежным и эффективным.  
  
 **Анализ проблем**  
  
 После создания тестового метода, проверяющего корректное списывание нужной суммы в методе `Debit` , вернемся к остальным вариантам исходного анализа.  
  
1.  Метод создает исключение `ArgumentOutOfRangeException` , если сумма по дебету превышает баланс.  
  
2.  Он также создает исключение `ArgumentOutOfRangeException` , если сумма по дебету меньше нуля.  
  
 **Создание методов теста**  
  
 Первая попытка создания тестового метода для решения этих проблем кажется перспективной:  
  
```csharp  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Мы используем атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> для подтверждения правильности созданного исключения. Данный атрибут приводит к тому, что тест не будет пройден, если не возникнет исключения `ArgumentOutOfRangeException` . Запуск теста как с положительными, так и с отрицательными значениями `debitAmount` , а также временное изменение тестируемого метода для возвращения универсального исключения <xref:System.ApplicationException> при размере списания меньше нуля показывает, что тест работает правильно. Чтобы проверить случай, когда размер списания превышает баланс, необходимо:  
  
1.  Создать новый метод теста с именем `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2.  Скопировать тело метода из `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` в новый метод.  
  
3.  Присвоить `debitAmount` значение, превышающее баланс.  
  
 **Запуск тестов**  
  
 Запуск двух методов с разными значениями для `debitAmount` показывает, что тесты корректно обрабатывают оставшиеся варианты. Запуск всех трех тестов позволяет убедиться в том, что все варианты в исходном анализе правильно охвачены тестами.  
  
 **Продолжение анализа**  
  
 Однако последние два тестовых метода вызывают некоторое беспокойство. Невозможно точно определить, какое условие тестируемого кода из всех тестовых запусков приводит к возникновению исключения. Желательно иметь способ различения этих двух условий. При дальнейшем анализе данной проблемы становится очевидным, что наличие сведений о нарушенном условии повышает надежность тестов. Также эти сведения, вероятно, могут быть полезны для создания рабочего механизма обработки ошибок при их возникновении в тестируемом методе. Получение дополнительной информации при создании методом исключения позволило бы установить данную связь, но атрибут `ExpectedException` не предоставляет эту информацию.  
  
 Еще раз посмотрев на тестируемый метод, можно заметить, что оба условных оператора используют конструктор `ArgumentOutOfRangeException` , который получает имя аргумента в качестве параметра:  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 Поиск в библиотеке MSDN позволяет обнаружить существование конструктора, сообщающего более детальную информацию. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` включает имя аргумента, значения аргумента и определяемое пользователем сообщение. Мы можем выполнить рефакторинг тестируемого метода для использования данного конструктора. Более того, можно использовать открытые для общего доступа члены типа для указания ошибок.  
  
 **Рефакторинг тестируемого кода**  
  
 Сначала определим две константы для сообщений об ошибках в области видимости класса:  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Изменим два условных оператора в методе `Debit` :  
  
```csharp  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Рефакторинг тестовых методов**  
  
 В данном тестовом методе сначала удалим атрибут `ExpectedException` . Вместо этого перехватываем возвращаемое исключение и проверяем, что оно было создано в правильном условном операторе. Однако теперь необходимо выбрать между двумя возможными вариантами для проверки оставшихся условий. Например, в методе `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` можно выполнить одно из следующих действий:  
  
-   Проверить, что свойство `ActualValue` исключения (второй параметр конструктора `ArgumentOutOfRangeException` ) больше начального баланса. В данном случае необходимо сравнить свойство `ActualValue` исключения со значением переменной `beginningBalance` метода теста, а также проверить, что значение `ActualValue` больше нуля.  
  
-   Проверить, что сообщение (третий параметр конструктора) включает `DebitAmountExceedsBalanceMessage` , определенное в классе `BankAccount` .  
  
 Метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> платформы модульных тестов Microsoft позволяет проверить второй параметр без вычислений, необходимых в первом случае.  
  
 Вторая попытка корректировки `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` может выглядеть следующим образом:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Повторное тестирование, переписывание и анализ**  
  
 При повторной проверке тестируемого метода с разными значениями получаем следующие факты:  
  
1.  При верном обнаружении ошибки с помощью утверждения, в котором `debitAmount` больше баланса, проверка утверждения `Contains` проходит успешно, исключение игнорируется и метод теста завершается успешно. Это соответствует ожидаемому поведению.  
  
2.  Если используется `debitAmount` меньше нуля, то проверка утверждения завершается неудачей, так как возвращается неверное сообщение об ошибке. Проверка утверждения также завершается неудачей, если ввести временное исключение `ArgumentOutOfRange` на другом шаге в коде тестируемого метода. Это тоже хорошо.  
  
3.  Если значение `debitAmount` допустимо (т.е. меньше баланса, но больше нуля), то исключение перехватывается, а утверждение никогда не сработает. Метод теста проходит успешно. Это не хорошо, поскольку метод теста должен был завершиться ошибкой в том случае, если исключение не создается.  
  
 Третьим фактом является ошибка в методе теста. Попытаемся разрешить проблему, добавив утверждение <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> в конце тестового метода для обработки случая, когда исключение не создается.  
  
 Однако повторное тестирование показывает, что тест теперь оказывается непройденным при перехватывании верного исключения. Оператор catch сбрасывает исключение и метод продолжает выполняться, приводя к ошибочному срабатыванию следующего утверждения. Чтобы разрешить эту новую проблему, добавим оператор `return` после `StringAssert`. Повторное тестирование подтверждает, что проблемы решены. Наша окончательная версия `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` выглядит следующим образом:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 В заключение скажем, что проведенная работа по улучшению тестируемого кода привела к созданию более надежных и информативных методов тестов. Однако более существенно то, что дополнительный анализ позволил улучшить тестируемый код в данном проекте.



