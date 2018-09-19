---
title: Справочник по API Microsoft.VisualStudio.TestTools.CppUnitTestFramework
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: mblome
manager: douge
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: 8309ee96b0948739124e0e23c4a57dd136f63362
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280926"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Справочник по API Microsoft.VisualStudio.TestTools.CppUnitTestFramework

В этом разделе перечислены открытые члены пространства имен `Microsoft::VisualStudio::CppUnitTestFramework`. С помощью этих интерфейсов API можно создавать модульные тесты для C++ на основе собственной платформы модульного тестирования Майкрософт. В конце раздела приводится [пример использования](#example).

 Файлы заголовков расположены в папке _папка_установки_Visual_Studio_2012[x86]_**\VC\UnitTest\include**.

 Файлы библиотек расположены в папке _папка_установки_Visual_Studio_2012[x86]_**\VC\UnitTest\lib**.

Пути к заголовкам и библиотекам автоматически настраиваются в собственном тестовом проекте.

##  <a name="In_this_topic"></a> Содержание раздела
 [CppUnitTest.h](#cppUnitTest_h)

-   [Создание тестовых классов и методов](#create_test_classes_and_methods)

-   [Инициализация и очистка](#Initialize_and_cleanup)

    -   [Методы тестов](#test_methods)

    -   [Тестовые классы](#test_classes)

    -   [Модули тестов](#test_modules)

-   [Создание атрибутов тестов](#create_test_attributes)

    -   [Атрибуты метода теста](#test_method_attributes)

    -   [Атрибуты тестового класса](#test_class_attributes)

    -   [Атрибуты модуля теста](#test_module_attributes)

    -   [Стандартные атрибуты](#pre_defined_attributes)

     [CppUnitTestAssert.h](#cppUnitTestAssert_h)

    -   [Общие утверждения](#general_asserts)

        -   [Проверка на равенство](#general_are_equal)

        -   [Проверка на неравенство](#general_are_not_equal)

        -   [Ссылаются на один и тот же объект](#general_are_same)

        -   [Не ссылаются на один и тот же объект](#general_are_not_same)

        -   [Имеет значение Null](#general_is_null)

        -   [Имеет значение не Null](#general_is_not_null)

        -   [Условие имеет значение true](#general_is_True)

        -   [Условие имеет значение false](#general_is_false)

        -   [Не пройден](#general_Fail)

    -   [Утверждения среды выполнения Windows](#winrt_asserts)

        -   [Проверка на равенство](#winrt_are_equal)

        -   [Ссылаются на один и тот же объект](#winrt_are_same)

        -   [Проверка на неравенство](#winrt_are_not_equal)

        -   [Не ссылаются на один и тот же объект](#winrt_are_not_same)

        -   [Имеет значение Null](#winrt_is_null)

        -   [Имеет значение не Null](#winrt_is_not_null)

    -   [Утверждения об исключениях](#exception_asserts)

        -   [Ожидается исключение](#expect_exception)

         [CppUnitTestLogger.h](#cppunittestlogger_h)

        -   [Ведение журнала](#logger)

        -   [Запись сообщения](#write_message)
    -    [Пример использования](#example)

##  <a name="cppUnitTest_h"></a> CppUnitTest.h

###  <a name="create_test_classes_and_methods"></a> Создание тестовых классов и методов

```cpp
TEST_CLASS(className)
```

 Требуется для каждого класса, содержащего методы тестов. Определяет *className* как тестовый класс. `TEST_CLASS` должен быть объявлен в области пространства имен.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Определяет *methodName* как метод теста. `TEST_METHOD` необходимо объявить в области класса метода.

###  <a name="Initialize_and_cleanup"></a> Инициализация и очистка

####  <a name="test_methods"></a> Методы тестов

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Определяет *methodName* в качестве метода, который выполняется перед выполнением каждого метода теста. `TEST_METHOD_INITIALIZE` может быть определен только один раз и должен находиться в тестовом классе.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Определяет *methodName* в качестве метода, который выполняется после выполнения каждого метода теста. `TEST_METHOD_CLEANUP` может быть определен только один раз в тестовом классе и должен быть определен в его области.

####  <a name="test_classes"></a> Тестовые классы

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Определяет *methodName* в качестве метода, который выполняется перед созданием каждого тестового класса. `TEST_CLASS_INITIALIZE` может быть определен только один раз в тестовом классе и должен быть определен в его области.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Определяет *methodName* в качестве метода, который выполняется после создания каждого тестового класса. `TEST_CLASS_CLEANUP` может быть определен только один раз в тестовом классе и должен быть определен в его области.

####  <a name="test_modules"></a> Модули тестов

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Определяет метод *methodName*, который выполняется, когда модуль загружен. `TEST_MODULE_INITIALIZE` может быть определен только один раз в модуле теста и должен быть объявлен в области пространства имен.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Определяет метод *methodName*, который выполняется, когда модуль выгружается. `TEST_MODULE_CLEANUP` может быть определен только один раз в модуле теста и должен быть объявлен в области пространства имен.

###  <a name="create_test_attributes"></a> Создание атрибутов тестов

####  <a name="test_method_attributes"></a> Атрибуты метода теста

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_METHOD_ATTRIBUTE`, в тестовый метод *testClassName*.

 Макрос `TEST_METHOD_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.

####  <a name="test_class_attributes"></a> Атрибуты тестового класса

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_CLASS_ATTRIBUTE`, в тестовый класс *testClassName*.

 Макрос `TEST_CLASS_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.

####  <a name="test_module_attributes"></a> Атрибуты модуля теста

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_MODULE_ATTRIBUTE`, в модуль теста *testModuleName*.

 Макрос `TEST_MODULE_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.

####  <a name="pre_defined_attributes"></a> Стандартные атрибуты
 Стандартные макросы атрибутов можно заменить макросами `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` или `TEST_MODULE_ATTRIBUTE`, описанными выше.

```cpp
TEST_OWNER(ownerAlias)
```

 Определите атрибут с именем `Owner` и значением *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Определите атрибут с именем `Description` и значением *description*.

```cpp
TEST_PRIORITY(priority)
```

 Определите атрибут с именем `Priority` и значением *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Определите атрибут с именем `WorkItem` и значением *workItem*.

```cpp
TEST_IGNORE()
```

 Определите атрибут с именем `Ignore` и значением `true`.

##  <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

###  <a name="general_asserts"></a> Общие утверждения

####  <a name="general_are_equal"></a> Проверка на равенство
 Проверяет, равны ли два объекта.

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет, равны ли два объекта типа double.

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет, равны ли два объекта типа float.

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет, равны ли две строки char*.

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет, равны ли две строки w_char*.

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_equal"></a> Проверка на неравенство
 Проверяет неравенство двух объектов типа double.

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет неравенство двух объектов типа float.

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет неравенство двух строк char*.

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет неравенство двух строк w_char*.

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Проверяет неравенство двух ссылок на основе оператора ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_same"></a> Ссылаются на один и тот же объект
 Проверяет, указывают ли две ссылки на один и тот же экземпляр объекта (идентификатор).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_same"></a> Не ссылаются на один и тот же объект
 Проверяет, что две ссылки не указывают на один и тот же экземпляр объекта (идентификатор).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_null"></a> Имеет значение Null
 Проверяет, имеет ли указатель значение NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_not_null"></a> Имеет значение не Null
 Проверяет, что указатель не равен NULL.

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_True"></a> Условие имеет значение true
 Проверяет, имеет ли условие значение true.

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_false"></a> Условие имеет значение false
 Проверяет, имеет ли условие значение alse.

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_Fail"></a> Не пройден
 Принудительно вернуть ошибку в тесте.

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

###  <a name="winrt_asserts"></a> Утверждения среды выполнения Windows

####  <a name="winrt_are_equal"></a> Проверка на равенство
 Проверяет, равны ли два указателя среды выполнения Windows.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Проверяет равенство двух строк Platform::String^.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_same"></a> Ссылаются на один и тот же объект
 Проверяет, указывают ли две ссылки среды выполнения Windows на один объект.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_equal"></a> Проверка на неравенство
 Проверяет неравенство двух указателей среды выполнения Windows.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Проверяет неравенство двух строк Platform::String^.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_same"></a> Не ссылаются на один и тот же объект
 Проверяет, что две ссылки среды выполнения Windows не указывают на один объект.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_null"></a> Имеет значение Null
 Проверяет, равен ли указатель среды выполнения Windows nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_not_null"></a> Имеет значение не Null
 Проверяет, что указатель среды выполнения Windows не равен nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

###  <a name="exception_asserts"></a> Утверждения об исключениях

####  <a name="expect_exception"></a> Ожидается исключение
 Проверяет, вызывает ли функция исключение.

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Проверяет, вызывает ли функция исключение.

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

##  <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

###  <a name="logger"></a> Ведение журнала
 Класс Logger содержит статические методы для записи в **окно вывода**.

###  <a name="write_message"></a> Запись сообщения
Запись строки в **окно вывода**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Пример
 Этот код является примером использования VSCppUnit. В него включены примеры метаданных атрибутов, фиксаций, модульных тестов с утверждениями и ведения пользовательских журналов.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>См. также

- [Модульное тестирование кода](../test/unit-test-your-code.md)
- [Написание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)

