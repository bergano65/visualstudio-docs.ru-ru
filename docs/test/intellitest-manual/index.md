---
title: Справочное руководство по IntelliTest | Инструменты тестирования для разработчиков Майкрософт
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f9534668ef5cf07388d6eefec9ef37a28593daaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977452"
---
# <a name="intellitest-reference-manual"></a>Справочное руководство по IntelliTest

## <a name="contents"></a>Описание

* **[Общие сведения о IntelliTest](introduction.md)**
  - [Основы IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Ограничения](introduction.md#limitations)
    * [Недетерминированность](introduction.md#nondeterminism)
    * [Параллелизм](introduction.md#concurrency)
    * [Машинный код](introduction.md#native-code)
    * [Платформа](introduction.md#platform)
    * [Язык](introduction.md#language)
    * [Символьная аналитика](introduction.md#symbolic-reasoning)
    * [Неправильные трассировки стека](introduction.md#incorrect-stack-traces)
  - [Дополнительные сведения](introduction.md#further-reading)<p>&nbsp;</p>

* **[Начало работы с IntelliTest](getting-started.md)**
  - [Важные атрибуты](getting-started.md#important-attributes)
  - [Важные статические вспомогательные классы](getting-started.md#helper-classes)<p>&nbsp;</p>

* **[Создание теста](test-generation.md)**
  - [Генераторы тестов](test-generation.md#test-generators)
  - [Параметризованное модульное тестирование](test-generation.md#parameterized-unit-testing)
  - [Общее параметризованное модульное тестирование](test-generation.md#generic-parameterized)
  - [Разрешение исключений](test-generation.md#allowing-exceptions)
  - [Тестирование внутренних типов](test-generation.md#internal-types)
  - [Предположения и утверждения](test-generation.md#assumptions-and-assertions)
  - [Предусловие](test-generation.md#precondition)
  - [Постусловие](test-generation.md#postcondition)
  - [Сбои при тестировании](test-generation.md#test-failures)
  - [Подготовка и демонтаж](test-generation.md#setup-teardown)
  - [Дополнительные сведения](test-generation.md#further-reading)<p>&nbsp;</p>

* **[Создание входных данных](input-generation.md)**
  - [Поиск решения для ограничений](input-generation.md#constraint-solver)
  - [Динамический объем протестированного кода](input-generation.md#dynamic-code-coverage)
  - [Целые числа и числа с плавающей запятой](input-generation.md#integers-and-floats)
  - [Объекты](input-generation.md#objects)
  - [Создание экземпляров существующих классов](input-generation.md#existing-classes)
  - [Видимость](input-generation.md#visibility)
  - [Параметризованный макет](input-generation.md#parameterized-mocks)
  - [Структуры](input-generation.md#structs)
  - [Массивы и строки](input-generation.md#arrays-and-strings)
  - [Получение дополнительных входных данных](input-generation.md#additional-inputs)
  - [Дополнительные сведения](input-generation.md#further-reading)<p>&nbsp;</p>

* **[Границы исследования](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

* **[Attribute Glossary](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Каскад параметров](settings-waterfall.md)**

* **[Статические вспомогательные классы](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

* **[Предупреждения и ошибки](warnings-and-errors.md)**
  - [Превышение значения MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [Превышение значения MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [Превышение значения MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [Превышение значения MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [Превышение значения MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [Превышение значения MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [Превышение значения MaxRunsWithoutNewTests](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Не удается конкретизировать решение](warnings-and-errors.md#cannot-concretize-solution)
  - [Требуется помощь по созданию объекта](warnings-and-errors.md#help-construct)
  - [Требуется помощь по поиску типов](warnings-and-errors.md#help-types)
  - [Предложение подходящих типов](warnings-and-errors.md#usable-type-guessed)
  - [Непредвиденная ошибка во время изучения](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Вызов неинструментированного метода](warnings-and-errors.md#uninstrumented-method-called)
  - [Вызов внешнего метода](warnings-and-errors.md#external-method-called)
  - [Вызов неинструментируемого метода](warnings-and-errors.md#uninstrumentable-method-called)
  - [Проблема тестирования](warnings-and-errors.md#testability-issue)
  - [Ограничение](warnings-and-errors.md#limitation)
  - [Обнаружено несовпадение вызовов](warnings-and-errors.md#observed-call-mismatch)
  - [Значение хранилось в статическом поле](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Хотите оставить отзыв?

Публикуйте свои идеи и запросы функций на сайте **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
