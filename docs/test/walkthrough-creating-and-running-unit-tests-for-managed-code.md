---
title: Создание и запуск модульных тестов для управляемого кода
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 26988b2fd74ae66bd1ef2724c55248371a81adf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922294"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода

В этой статье приводится подробное описание процесса создания, запуска и настройки набора модульных тестов с помощью платформы модульных тестов Майкрософт для управляемого кода и **обозревателя тестов** Visual Studio. В руководстве производится создание проекта C#, находящегося в стадии разработки, создание тестов для проверки его кода, запуск тестов и изучение результатов. После этого производится изменение кода проекта и повторный запуск тестов.

> [!NOTE]
> В этом пошаговом руководстве используется платформа модульных тестов Microsoft для управляемого кода. **Обозреватель тестов** также может запускать тесты c платформ модульных тестов стороннего производителя, которые имеют адаптеры для **обозревателя тестов**. Дополнительные сведения см. в разделе [Установка платформ модульного тестирования сторонних поставщиков](../test/install-third-party-unit-test-frameworks.md).

Сведения о запуске тестов из командной строки см. в разделе [Параметры командной строки VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Предварительные требования

- Проект "Банк". См. раздел [Пример проекта для создания модульных тестов](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Создайте проект для тестирования

1. Запустите Visual Studio.

2. В меню **Файл** выберите пункт **Создать** > **Проект**.

   Откроется диалоговое окно **Новый проект** .

3. В области **Установленные шаблоны**выберите шаблон **Visual C#**.

4. В списке типов приложения выберите пункт **Библиотека классов**.

5. В поле **Имя** введите **Bank** и нажмите **OK**.

   Будет создан новый проект Bank. Этот проект отобразится в **обозревателе решений**, а его файл *Class1.cs* откроется в редакторе кода.

   > [!NOTE]
   > Если файл *Class1.cs* не откроется в редакторе кода, дважды щелкните *Class1.cs* в **обозревателе решений**, чтобы открыть его.

6. Скопируйте исходный текст из раздела [Пример проекта для создания модульных тестов](../test/sample-project-for-creating-unit-tests.md) и замените скопированным текстом исходное содержимое файла *Class1.cs*.

7. Сохранение файла как *BankAccount.cs*.

8. В меню **Сборка** выберите **Собрать решение**.

Будет создан проект с именем "Bank". Он содержит исходный код, подлежащий тестированию, и средства для его тестирования. Пространство имен BankAccountNS проекта "Bank", содержит открытый класс "BankAccount", методы которого будут тестироваться в приведенных ниже процедурах.

В этой статье проводится тестирование на примере метода Debit. Метод Debit вызывается, когда денежные средства снимаются со счета. Так выглядит определение метода:

```csharp
// Method to be tested.
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

## <a name="create-a-unit-test-project"></a>Создание проекта модульного теста

1. В меню **Файл** выберите **Добавить** > **Создать проект**.

   > [!TIP]
   > Существует несколько способов добавить дополнительный проект в существующее решение. В **обозревателе решений** щелкните решение правой кнопкой мыши и выберите пункты **Добавить** > **Создать проект**. Или выберите **Файл** > **Создать** > **Проект**, а затем в диалоговом окне **Создать проект** выберите **Добавить решение**:
   >
   > ![Добавление параметра решения в диалоговом окне создания проекта](media/add-to-solution.png)

2. В диалоговом окне **Новый проект** разверните узлы **Установленные** и **Visual C#** и выберите **Тест**.

3. В списке шаблонов выберите **Проект модульного теста**.

4. В поле **Имя** введите `BankTests`, а затем нажмите кнопку **ОК**.

   Проект **BankTests** добавляется в решение **Банк**.

5. В проекте **BankTests** добавьте ссылку на проект **Банк**.

   В **обозревателе решений** щелкните **Ссылки** в проекте **BankTests**, а затем выберите в контекстном меню **Добавить ссылку**.

6. В диалоговом окне **Диспетчер ссылок** разверните **Решение** и проверьте элемент **Банк**.

## <a name="create-the-test-class"></a>Создание тестового класса

Создание тестового класса, чтобы проверить класс `BankAccount`. Можно использовать *UnitTest1.cs*, созданный в шаблоне проекта, но лучше дать файлу и классу более описательные имена. Можно сделать это за один шаг, переименовав файл в **обозревателе решений**.

### <a name="rename-a-class-file"></a>Переименование файла класса

В **обозревателе решений** выберите файл *UnitTest1.cs* в проекте BankTests. В контекстном меню выберите команду **Переименовать**, а затем переименуйте файл в *BankAccountTests.cs*. Выберите **Да** в диалоговом окне, предлагающем переименовать все ссылки на элемент кода `UnitTest1` в проекте.

Этот шаг изменяет имя класса на `BankAccountTests`. Файл *BankAccountTests.cs* теперь содержит следующий код:

```csharp
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>Добавление оператора using в тестируемый проект

Можно также добавить оператор `using` в класс, чтобы тестируемый проект можно было вызывать без использования полных имен. Вверху файла класса добавьте:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Требования к тестовому классу

Минимальные требования к тестовому классу следующие:

- Атрибут `[TestClass]` является обязательным для платформы модульных тестов Microsoft для управляемого кода в любом классе, содержащем методы модульных тестов, которые необходимо выполнить в обозревателе тестов.

- Каждый метод теста, предназначенный для запуска в обозревателе тестов, должен иметь атрибут `[TestMethod]`.

Можно иметь другие классы в проекте модульного теста, которые не содержат атрибута `[TestClass]` , а также иметь другие методы в тестовых классах, у которых атрибут — `[TestMethod]` . Можно использовать эти другие классы и методы в методах теста.

## <a name="create-the-first-test-method"></a>Создание первого тестового метода

В этой процедуре мы напишем методы модульного теста для проверки поведения метода `Debit` класса `BankAccount`. Метод `Debit` приведен выше в этой статье.

Существует по крайней мере три поведения, которые требуется проверить:

- Метод создает исключение <xref:System.ArgumentOutOfRangeException> , если сумма по дебету превышает баланс.

- Метод создает исключение <xref:System.ArgumentOutOfRangeException>, если сумма по дебету меньше нуля.

- Если значение дебета допустимо, то метод вычитает сумму дебета из баланса счета.

> [!TIP]
> Метод по умолчанию `TestMethod1` можно удалять, так как он не используется в этом руководстве.

### <a name="to-create-a-test-method"></a>Создание метода теста

Первый тест проверяет, снимается ли со счета нужная сумма при допустимом размере кредита (со значением меньшим, чем баланс счета, и большим, чем ноль). Добавьте следующий метод в этот класс `BankAccountTests` :

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Метод очень прост: он создает новый объект `BankAccount` с начальным балансом, а затем снимает допустимое значение. Он использует метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, чтобы проверить, что конечный баланс соответствует ожидаемому.

### <a name="test-method-requirements"></a>Требования к методу теста

Метод теста должен удовлетворять следующим требованиям:

- Он декорируется атрибутом `[TestMethod]`.

- Он возвращает `void`.

- Он не должен иметь параметров.

## <a name="build-and-run-the-test"></a>Сборка и запуск теста

1. В меню **Построение** выберите **Построить решение**.

   Если ошибок нет, появится **обозреватель тестов** с элементом **Debit_WithValidAmount_UpdatesBalance** в группе **Незапускавшиеся тесты**.

   > [!TIP]
   > Если **обозреватель тестов** не откроется после успешной сборки, выберите в меню пункт **Тест**, щелкните **Windows**, а затем — **Обозреватель тестов**.

2. Выберите **Запустить все** , чтобы выполнить тест. Во время выполнения теста в верхней части окна отображается анимированная строка состояния. По завершении тестового запуска строка состояния становится зеленой, если все методы теста успешно пройдены, или красной, если какие-либо из тестов не пройдены.

3. В данном случае тест пройден не будет. Метод теста будет перемещен в группу **Неудачные тесты**. Выберите этот метод в **обозревателе тестов** для просмотра сведений в нижней части окна.

## <a name="fix-your-code-and-rerun-your-tests"></a>Исправление кода и повторный запуск тестов

### <a name="analyze-the-test-results"></a>Анализ результатов теста

Результат теста содержит сообщение, описывающее возникшую ошибку. Для метода `AreEqual` сообщение отражает ожидаемый результат (параметр **Ожидается\<*значение*>**) и фактически полученный (параметр **Фактическое\<*значение*>**). Ожидалось, что баланс уменьшится, а вместо этого он увеличился на сумму списания.

Модульный тест обнаружил ошибку: сумма списания *добавляется* на баланс счета, вместо того чтобы *вычитаться*.

### <a name="correct-the-bug"></a>Исправление ошибки

Для исправления ошибки замените строку:

```csharp
m_balance += amount;
```

на:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Повторный запуск теста

В **обозревателе тестов** выберите **Запустить все**, чтобы запустить тест повторно. Красно-зеленая строка состояния станет зеленой, сигнализируя о том, что тест пройден, а сам тест будет перемещен в группу **Пройденные тесты**.

## <a name="use-unit-tests-to-improve-your-code"></a>Использование модульных тестов для улучшения кода

В этом разделе рассматривается, как последовательный процесс анализа, разработки модульных тестов и рефакторинга может помочь сделать рабочий код более надежным и эффективным.

### <a name="analyze-the-issues"></a>Анализ проблем

Мы создали тестовый метод для подтверждения того, что допустимая сумма правильно вычитается в методе `Debit`. Теперь проверим, что метод создает исключение <xref:System.ArgumentOutOfRangeException>, если сумма по дебету:

- больше баланса или
- меньше нуля.

### <a name="create-the-test-methods"></a>Создание методов теста

Создадим метод теста для проверки правильного поведения в случае, когда сумма по дебету меньше нуля:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Мы используем атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> для подтверждения правильности созданного исключения. Данный атрибут приводит к тому, что тест не будет пройден, если не возникнет исключения <xref:System.ArgumentOutOfRangeException> . Если временно изменить тестируемый метод для вызова более общего исключения <xref:System.ApplicationException> при значении суммы по дебету меньше нуля, то тест работает правильно &mdash; то есть завершается неудачно.

Чтобы проверить случай, когда размер списания превышает баланс, выполните следующие действия:

1. Создать новый метод теста с именем `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Скопировать тело метода из `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` в новый метод.

3. Присвоить `debitAmount` значение, превышающее баланс.

### <a name="run-the-tests"></a>Запуск тестов

Запуск двух методов теста показывает, что тесты работают правильно.

### <a name="continue-the-analysis"></a>Продолжение анализа

Однако последние два тестовых метода вызывают беспокойство. Нельзя быть уверенным, какое именно условие тестируемого метода создает исключение при запуске любого из тестов. Если каким-либо способом разделить эти два условия, а именно отрицательную сумму по дебету и сумму, большую, чем баланс, то это увеличит достоверность проведения тестов.

Еще раз посмотрев на тестируемый метод и заметив, что оба условных оператора используют конструктор `ArgumentOutOfRangeException`, который просто получает имя аргумента в качестве параметра:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Так выглядит конструктор, который можно использовать для сообщения более детальной информации: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> включает имя аргумента, значения аргумента и определяемое пользователем сообщение. Мы можем выполнить рефакторинг тестируемого метода для использования данного конструктора. Более того, можно использовать открытые для общего доступа члены типа для указания ошибок.

### <a name="refactor-the-code-under-test"></a>Рефакторинг тестируемого кода

Сначала определим две константы для сообщений об ошибках в области видимости класса. Добавьте это в тестируемый класс BankAccount:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Затем изменим два условных оператора в методе `Debit`:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Рефакторинг тестовых методов

Удалим атрибут `ExpectedException` метода теста, и вместо этого будем перехватывать исключение и проверять соответствующее ему сообщение. Метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> обеспечивает возможность сравнения двух строк.

В этом случае метод `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` может выглядеть следующим образом:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Повторное тестирование, переписывание и анализ

Предположим, что в тестируемом методе есть ошибка, и метод `Debit` даже не создает исключение <xref:System.ArgumentOutOfRangeException>, не говоря уже о выводе правильного сообщения с исключением. В этом случае метод теста не сможет обработать этот случай. Если значение `debitAmount` допустимо (то есть меньше баланса, но больше нуля), то исключение не перехватывается, а утверждение никогда не сработает. Однако метод теста проходит успешно. Это нехорошо, поскольку метод теста должен был завершиться с ошибкой в том случае, если исключение не создается.

Это является ошибкой в методе теста. Для решения этой проблемы добавим утверждение <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> в конце тестового метода для обработки случая, когда исключение не создается.

Однако повторный запуск теста показывает, что тест теперь оказывается *непройденным* при перехватывании верного исключения. Блок `catch` перехватывает исключение, но метод продолжает выполняться, и в нем происходит сбой на новом утверждении <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Чтобы разрешить эту проблему, добавим оператор `return` после `StringAssert` в блоке `catch`. Повторный запуск теста подтверждает, что проблема устранена. Окончательная версия метода `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` выглядит следующим образом:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Усовершенствования тестового кода привели к созданию более надежных и информативных методов теста. Но что более важно, в результате был также улучшен тестируемый код.
