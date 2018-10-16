---
title: Использование пространства имен Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: cc643f8bd8addefc2bec4c62645e8091aaedc11c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291243"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Использование пространства имен Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе перечислены открытые члены пространства имен `Microsoft::VisualStudio::CppUnitTestFramework`.  
  
 Файлы заголовков расположены в папке _папка_установки_Visual_Studio_2012[x86]_**\VC\UnitTest\include**.  
  
 Файлы библиотек расположены в папке _папка_установки_Visual_Studio_2012[x86]_**\VC\UnitTest\lib**.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
-   [Создание тестовых классов и методов](#BKMK_Create_test_classes_and_methods)  
  
-   [Инициализация и очистка](#BKMK_Initialize_and_cleanup)  
  
    -   [Методы тестов](#BKMK_Test_methods)  
  
    -   [Тестовые классы](#BKMK_Test_classes)  
  
    -   [Модули тестов](#BKMK_Test_modules)  
  
-   [Создание атрибутов тестов](#BKMK_Create_test_attributes)  
  
    -   [Атрибуты метода теста](#BKMK_Test_method_attributes)  
  
    -   [Атрибуты тестового класса](#BKMK_Test_class_attributes)  
  
    -   [Атрибуты модуля теста](#BKMK_Test_module_attributes)  
  
    -   [Стандартные атрибуты](#BKMK_Pre_defined_attributes)  
  
     [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
    -   [Общие утверждения](#BKMK_General_Asserts)  
  
        -   [Проверка на равенство](#BKMK_General_Are_Equal)  
  
        -   [Проверка на неравенство](#BKMK_General_Are_Not_Equal)  
  
        -   [Ссылаются на один и тот же объект](#BKMK_General_Are_Same)  
  
        -   [Не ссылаются на один и тот же объект](#BKMK_General_Are_Not_Same)  
  
        -   [Имеет значение Null](#BKMK_General_Is_Null)  
  
        -   [Имеет значение не Null](#BKMK_General_Is_Not_Null)  
  
        -   [Условие имеет значение true](#BKMK_General_Is_True)  
  
        -   [Условие имеет значение false](#BKMK_General_Is_False)  
  
        -   [Не пройден](#BKMK_General_Fail)  
  
    -   [Утверждения среды выполнения Windows](#BKMK_WinRT_Asserts)  
  
        -   [Проверка на равенство](#BKMK_WinRT_Are_Equal)  
  
        -   [Ссылаются на один и тот же объект](#BKMK_WinRT_Are_Same)  
  
        -   [Проверка на неравенство](#BKMK_WinRT_Are_Not_Equal)  
  
        -   [Не ссылаются на один и тот же объект](#BKMK_WinRT_Are_Not_Same)  
  
        -   [Имеет значение Null](#BKMK_WinRT_Is_Null)  
  
        -   [Имеет значение не Null](#BKMK_WinRT_Is_Not_Null)  
  
    -   [Утверждения об исключениях](#BKMK_Exception_Asserts)  
  
        -   [Ожидается исключение](#BKMK_Expect_Exception)  
  
         [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
        -   [Ведение журнала](#BKMK_Logger)  
  
        -   [Запись сообщения](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Создание тестовых классов и методов  
  
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
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Инициализация и очистка  
  
####  <a name="BKMK_Test_methods"></a> Методы тестов  
  
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
  
####  <a name="BKMK_Test_classes"></a> Тестовые классы  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Определяет *methodName* в качестве метода, который выполняется после создания каждого тестового класса. `TEST_CLASS_INITIALIZE` может быть определен только один раз в тестовом классе и должен быть определен в его области.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Определяет *methodName* в качестве метода, который выполняется после создания каждого тестового класса. `TEST_CLASS_CLEANUP` может быть определен только один раз в тестовом классе и должен быть определен в его области.  
  
####  <a name="BKMK_Test_modules"></a> Модули тестов  
  
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
  
###  <a name="BKMK_Create_test_attributes"></a> Создание атрибутов тестов  
  
####  <a name="BKMK_Test_method_attributes"></a> Атрибуты метода теста  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_METHOD_ATTRIBUTE`, в тестовый метод *testClassName*.  
  
 Макрос `TEST_METHOD_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Атрибуты тестового класса  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_CLASS_ATTRIBUTE`, в тестовый класс *testClassName*.  
  
 Макрос `TEST_CLASS_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Атрибуты модуля теста  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Добавляет атрибуты, определенные с одним или несколькими макросами `TEST_MODULE_ATTRIBUTE`, в модуль теста *testModuleName*.  
  
 Макрос `TEST_MODULE_ATTRIBUTE` определяет атрибут с именем *attributeName* и значением *attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Стандартные атрибуты  
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
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Общие утверждения  
  
####  <a name="BKMK_General_Are_Equal"></a> Проверка на равенство  
 Проверяет, равны ли два объекта.  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет, равны ли два объекта типа double.  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет, равны ли два объекта типа float.  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет, равны ли две строки char*.  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет, равны ли две строки w_char*.  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> Проверка на неравенство  
 Проверяет неравенство двух объектов типа double.  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет неравенство двух объектов типа float.  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет неравенство двух строк char*.  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет неравенство двух строк w_char*.  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Проверяет неравенство двух ссылок на основе оператора ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> Ссылаются на один и тот же объект  
 Проверяет, указывают ли две ссылки на один и тот же экземпляр объекта (идентификатор).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> Не ссылаются на один и тот же объект  
 Проверяет, что две ссылки не указывают на один и тот же экземпляр объекта (идентификатор).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> Имеет значение Null  
 Проверяет, имеет ли указатель значение NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> Имеет значение не Null  
 Проверяет, что указатель не равен NULL.  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> Условие имеет значение true  
 Проверяет, имеет ли условие значение true.  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> Условие имеет значение false  
 Проверяет, имеет ли условие значение alse.  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Не пройден  
 Принудительно вернуть ошибку в тесте.  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Утверждения среды выполнения Windows  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> Проверка на равенство  
 Проверяет, равны ли два указателя среды выполнения Windows.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Проверяет равенство двух строк Platform::String^.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> Ссылаются на один и тот же объект  
 Проверяет, указывают ли две ссылки среды выполнения Windows на один объект.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> Проверка на неравенство  
 Проверяет неравенство двух указателей среды выполнения Windows.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Проверяет неравенство двух строк Platform::String^.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> Не ссылаются на один и тот же объект  
 Проверяет, что две ссылки среды выполнения Windows не указывают на один объект.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> Имеет значение Null  
 Проверяет, равен ли указатель среды выполнения Windows nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> Имеет значение не Null  
 Проверяет, что указатель среды выполнения Windows не равен nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Утверждения об исключениях  
  
####  <a name="BKMK_Expect_Exception"></a> Ожидается исключение  
 Проверяет, вызывает ли функция исключение.  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Проверяет, вызывает ли функция исключение.  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Ведение журнала  
 Класс Logger содержит статические методы для записи.  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> Запись сообщения  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## <a name="example"></a>Пример  
 Далее приведен пример кода.  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
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
 [Модульное тестирование кода](../test/unit-test-your-code.md)   
 [Модульное тестирование машинного кода с использованием обозревателя тестов](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Модульное тестирование существующих приложений C++ с использованием обозревателя тестов](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)



