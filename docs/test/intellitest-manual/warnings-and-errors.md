---
title: Предупреждения и ошибки | Инструмент тестирования для разработчиков Microsoft IntelliTest
description: В этой статье содержатся предупреждения и ошибки IntelliTest, упорядоченные по категориям, с описаниями для каждого предупреждения и ошибки.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 69fea3216602bf78084ef9141280fd4ba7aa4c57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920409"
---
# <a name="warnings-and-errors"></a>Предупреждения и ошибки

## <a name="warnings-and-errors-by-category"></a>Предупреждения и ошибки по категориям

* **границы,**
  * [Превышение значения MaxBranches](#maxbranches-exceeded)
  * [Превышение значения MaxConstraintSolverTime](#maxconstraintsolvertime-exceeded)
  * [Превышение значения MaxConditions](#maxconditions-exceeded)
  * [Превышение значения MaxCalls](#maxcalls-exceeded)
  * [Превышение значения MaxStack](#maxstack-exceeded)
  * [Превышение значения MaxRuns](#maxruns-exceeded)
  * [Превышение значения MaxRunsWithoutNewTests](#maxrunswithoutnewtests-exceeded)

* **Поиск решения для ограничений**
  * [Не удается конкретизировать решение](#cannot-concretize-solution)

* **Домены или среда выполнения**
  * [Требуется помощь по созданию объекта](#help-construct)
  * [Требуется помощь по поиску типов](#help-types)
  * [Предложение подходящих типов](#usable-type-guessed)

* **Выполнение**
  * [Непредвиденная ошибка во время изучения](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Инструментирование**
  * [Вызов неинструментированного метода](#uninstrumented-method-called)
  * [Вызов внешнего метода](#external-method-called)
  * [Вызов неинструментируемого метода](#uninstrumentable-method-called)
  * [Проблема тестирования](#testability-issue)
  * [Ограничения](#limitation)

* **Интерпретатор**
  * [Обнаружено несовпадение вызовов](#observed-call-mismatch)
  * [Значение хранилось в статическом поле](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>Превышение значения MaxBranches

IntelliTest ограничивает длину любого пути выполнения, изучаемого IntelliTest во время [создания входных данных](input-generation.md). Эта функция предотвращает зависание IntelliTest, когда программа переходит в бесконечный цикл.

В этом пределе учитывается каждая условная и безусловная ветвь выполняемого и отслеживаемого кода, включая ветви, которые не зависят от входных параметров [параметризованного модульного теста](test-generation.md#parameterized-unit-testing).

Например, следующий код использует ветви до 100:

```csharp
for (int i=0; i<100; i++) { }
```

Можно изменить параметр **MaxBranches** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Следующий пример снимает это ограничение:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Вы также можете задать параметр **TestExcludePathBoundsExceeded**, чтобы указать IntelliTest на способы устранения подобных проблем.

В коде теста можно использовать [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue), чтобы игнорировать ограничения, созданные условием цикла:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>Превышение значения MaxConstraintSolverTime

IntelliTest использует [поиск решения для ограничений](input-generation.md#constraint-solver) для вычисления новых входных данных теста. Поиск решения для ограничений может занимать очень много времени, поэтому IntelliTest позволяет настроить границы, в частности, **MaxConstraintSolverTime**.

Для многих приложений значительное увеличение этого время ожидания не обеспечивает больший охват. Это обусловлено тем, что большинство ситуаций, когда истечение времени ожидания было вызвано системой ограничений, не имеют решений. Однако IntelliTest может быть не в состоянии определить нецелесообразность обработки, не проверив все возможные решения, что приведет к истечению времени ожидания.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>Превышение значения MaxConditions

IntelliTest ограничивает длину любого пути выполнения, изучаемого IntelliTest во время [создания входных данных](input-generation.md). Эта функция предотвращает зависание IntelliTest, когда программа переходит в бесконечный цикл.

В этом пределе учитывается каждая условная ветвь, зависящая от входных параметров [параметризованного модульного теста](test-generation.md#parameterized-unit-testing).

Например, каждый путь в следующем коде использует **n+1** условий:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Можно изменить параметр **MaxConditions** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Пример:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Вы также можете задать параметр **TestExcludePathBoundsExceeded**, чтобы указать IntelliTest на способы устранения подобных проблем.

Вы можете использовать [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue), чтобы игнорировать ограничения, созданные условием цикла:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>Превышение значения MaxCalls

IntelliTest ограничивает длину любого пути выполнения, изучаемого IntelliTest во время [создания входных данных](input-generation.md). Эта функция предотвращает зависание IntelliTest, когда программа переходит в бесконечный цикл.

В этом пределе учитывается каждый вызов (прямой, косвенный, виртуальный или переход) выполняемого и отслеживаемого кода.

Можно изменить параметр **MaxCalls** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Следующий пример снимает это ограничение:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Вы также можете задать параметр **TestExcludePathBoundsExceeded**, чтобы указать IntelliTest на способы устранения подобных проблем.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>Превышение значения MaxStack

IntelliTest ограничивает размер стека вызовов для любого пути выполнения, изучаемого IntelliTest во время [создания входных данных](input-generation.md). Эта функция предотвращает завершение работы IntelliTest при переполнении стека.

Можно изменить параметр **MaxStack** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Следующий пример снимает это ограничение (что не рекомендуется делать):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Вы также можете задать параметр **TestExcludePathBoundsExceeded**, чтобы указать IntelliTest на способы устранения подобных проблем.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>Превышение значения MaxRuns

IntelliTest ограничивает число путей выполнения, изучаемых IntelliTest во время [создания входных данных](input-generation.md). Эта функция обеспечивает завершение работы IntelliTest, когда программа содержит циклы или рекурсию.

Может оказаться так, что IntelliTest не выдает новый тестовый случай при каждом запуске параметризованного теста с определенными входными данными. Дополнительные сведения см. в разделе [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Можно изменить параметр **MaxRuns** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Следующий пример снимает это ограничение (что не рекомендуется делать):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>Превышение значения MaxRunsWithoutNewTests

IntelliTest ограничивает число путей выполнения, изучаемых IntelliTest во время [создания входных данных](input-generation.md). Эта функция обеспечивает завершение работы IntelliTest, когда программа содержит циклы или рекурсию.

Может оказаться так, что IntelliTest не выдает новый тестовый случай при каждом запуске параметризованного теста с определенными входными данными. Дополнительные сведения см. в разделе [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Хотя на начальном этапе IntelliTest часто находит множество интересных входных данных тестов, через некоторое время он может перестать выдавать какие-либо новые тесты. Этот параметр определяет, как долго IntelliTest может пытаться найти другой релевантный входной параметр теста.

Можно изменить параметр **MaxRunsWithoutNewTests** атрибута, производного от **PexSettingsAttributeBase**, такого как [PexClass](attribute-glossary.md#pexclass) или [PexMethod](attribute-glossary.md#pexmethod). Следующий пример снимает это ограничение (что не рекомендуется делать):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Не удается конкретизировать решение

Эта ошибка часто является следствием более ранней ошибки. IntelliTest использует [поиск решения для ограничений](input-generation.md#constraint-solver) для определения новых входных данных теста. Иногда [поиск решения для ограничений](input-generation.md#constraint-solver) предлагает неверные входные данные. Это может произойти в следующих случаях:

* когда некоторые ограничения неизвестны;
* когда значения создаются определенным пользователем образом, вызывая ошибки в пользовательском коде;
* когда некоторые из используемых типов имеют логику инициализации, неподконтрольную IntelliTest (например, COM-классов).

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Требуется помощь по созданию объекта

IntelliTest [создает входные данные теста](input-generation.md), часть которых может быть представлена объектами с полями.
В этом случае IntelliTest пытается создать экземпляр класса, имеющий частное поле, и предполагает, что интересующее поведение программы возникнет, когда это частное поле имеет определенное значение.

Хотя это можно сделать с помощью отражения, IntelliTest не производит объекты с произвольными значениями полей.
В подобных случаях инструмент полагается на указания пользователя о том, как использовать открытые методы класса для создания объекта и перевода его в состояние, где его частное поле имеет необходимое значение.

Сведения о том, как можно помочь IntelliTest при создании таких объектов, см. в разделе [Создание экземпляров существующих классов](input-generation.md#existing-classes).

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Требуется помощь по поиску типов

IntelliTest [создает входные данные теста](input-generation.md) для любого типа .NET Framework. В этом случае IntelliTest пытается создать экземпляр, который является производным от абстрактного класса или реализует абстрактный интерфейс, при этом IntelliTest не знает ни об одном типе, реализующем подобные ограничения.

Вы можете помочь IntelliTest, указав один или несколько типов, которые соответствуют данным ограничениям. В общем случае подходит один из следующих атрибутов:

* **PexUseTypeAttribute**, который указывает на определенный тип.

  Например, если IntelliTest сообщает, что не знает ни о каких типах, которые можно назначить **System.Collections.IDictionary**, вы можете помочь инструменту, присоединив к тесту (или к классу фикстуры) следующий **PexUseTypeAttribute**:

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Атрибут уровня сборки**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Предложение подходящих типов

IntelliTest [создает входные данные теста](input-generation.md) для любых типов .NET Framework. Если тип является абстрактным или интерфейсом, IntelliTest нужно выбрать его конкретную реализацию. Для этого инструменту требуется знать, какие типы существуют.

Это предупреждение отображается, когда IntelliTest проанализировал некоторые из указанных сборок и нашел тип реализации, но не уверен, следует ли использовать данный тип либо искать более подходящие типы в другом месте. IntelliTest просто выбирает наиболее уместный тип.

Чтобы избежать отображения этого предупреждения, можно принять выбранный IntelliTest тип или помочь инструменту использовать другие типы, добавив соответствующий [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Непредвиденная ошибка во время изучения

Во время изучения теста было захвачено непредвиденное исключение.

Сообщите об [этой ошибке](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

В пользовательском коде возникло исключение. Просмотрите трассировку стека и устраните ошибку в коде.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Вызов неинструментированного метода

IntelliTest [создает входные данные теста](input-generation.md), отслеживая выполнение программы. Очень важно обеспечить правильное инструментирование соответствующего кода, чтобы IntelliTest мог отслеживать его поведение.

Это предупреждение появляется, когда инструментированный код вызывает методы в другой, неинструментированной сборке.
Если вы хотите, чтобы IntelliTest изучил их взаимодействие, нужно также инструментировать и другую сборку (или ее части).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Вызов внешнего метода

IntelliTest [создает входные данные теста](input-generation.md), отслеживая выполнение приложений .NET.
IntelliTest не может создавать значимые входные данные теста для кода, который написан не на языке .NET.

Это предупреждение возникает, когда инструментированный код вызывает неуправляемый собственный метод, который IntelliTest не может проанализировать. Если вы хотите, чтобы IntelliTest изучил их взаимодействие, нужно также макетировать неуправляемый метод.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Вызов неинструментируемого метода

IntelliTest [создает входные данные теста](input-generation.md), отслеживая выполнение приложений .NET. Однако существуют некоторые методы, которые IntelliTest может отслеживать по техническим причинам. Например, IntelliTest не может отслеживать статический конструктор.

Это предупреждение возникает, когда инструментированный код вызывает метод, который IntelliTest не может отслеживать.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Проблема тестирования

IntelliTest [создает входные данные теста](input-generation.md), отслеживая выполнение программы. Он может создавать соответствующие входные данные теста, только когда программа является детерминированной, а соответствующее поведение управляется входными данными теста.

Это предупреждение появляется из-за того, что во время выполнения тестового случая был вызван метод, который ведет себя недетерминированным образом или взаимодействует с окружением. В качестве примеров можно привести методы **System.Random** и **System.IO.File**. Если вы хотите, чтобы IntelliTest создавал более значимые входные данные теста, следует макетировать методы, помеченные IntelliTest как имеющие проблемы с тестированием.

<a name="limitation"></a>
## <a name="limitation"></a>Ограничение

IntelliTest [создает входные данные теста](input-generation.md) с помощью [поиска решения для ограничения](input-generation.md#constraint-solver).
Однако некоторые операции выходят из области действия [поиска решения для ограничений](input-generation.md#constraint-solver).
Сейчас к ним относятся следующие:

* большинство операций с плавающей запятой (для чисел с плавающей запятой поддерживаются только некоторые линейные арифметические операции);
* преобразования между целыми числами и числами с плавающей запятой;
* все операции с типом **System.Decimal**.

Это предупреждение возникает, когда выполняемый код производит операцию или вызывает метод, которые IntelliTest не может интерпретировать.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Обнаружено несовпадение вызовов

IntelliTest [создает входные данные теста](input-generation.md), отслеживая выполнение программы. Однако IntelliTest может быть не в состоянии отслеживать все инструкции. Например, он не может отслеживать машинный и неинструментированный код.

Если IntelliTest не может отслеживать код, он не может создать для него входные данные теста.
Часто IntelliTest не знает, что не может отслеживать метод, до возврата данных в рамках вызова этого метода. Однако причиной этого предупреждения является следующее:

* IntelliTest отслеживал некий код, который выполнил вызов неинструментированного метода.
* Неинструментированный метод вызвал инструментированный метод.
* IntelliTest отслеживает инструментированный метод, который был вызван.

IntelliTest не знает, что сделал промежуточный неинструментированный метод, поэтому может быть не в состоянии создать входные данные теста, относящиеся к вложенному инструментированному вызову.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Значение хранилось в статическом поле

IntelliTest может систематически определять [релевантные входные данные теста](input-generation.md), только если модульный тест является детерминированным, то есть всегда ведет себя одинаково при тех же самых входных данных теста. В частности, это означает, что тест должен оставить систему в состоянии, допускающем повторное выполнение данного теста.
В оптимальном случае модульный тест не должен изменять глобальное состояние, однако требуется макетировать все взаимодействия с глобальными объектами.

Это предупреждение указывает на то, что статическое поле было изменено. Это может быть причиной недетерминированного поведения теста.

В некоторых ситуациях изменение статического поля является допустимым:

* когда входные данные теста требуют от кода установки или очистки для отмены изменений;
* когда поле инициируется только один раз, после чего значение не меняется.

<a name="report-bug"></a>

## <a name="got-feedback"></a>Хотите отправить отзыв?

Делитесь своими идеями и пожеланиями относительно новых функций в [сообществе разработчиков](https://aka.ms/feedback/suggest?space=8).
