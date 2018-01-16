---
title: "Использование Boost.Test для C++ в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Использование Boost.Test для C++ в Visual Studio

В **Visual Studio 2017 версии 15.5** и более поздних адаптер теста Boost.Test интегрирован в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**.

![Адаптер теста для Boost.Test](media/cpp-boost-component.png "Адаптер теста для компонента Boost.Test")

Если у вас не установлена рабочая нагрузка **Разработка классических приложений на C++**, откройте **установщик Visual Studio** и нажмите кнопку **Изменить**. Выберите рабочую нагрузку **Разработка классических приложений на C++**, а затем нажмите кнопку **Изменить**.

## <a name="install-boost"></a>Установка Boost

Для Boost.Test требуется [Boost](http://www.boost.org/). Если у вас не установлен Boost, рекомендуем воспользоваться диспетчером пакетов Vcpkg.

1. Следуйте инструкциям в статье [vcpkg: диспетчер пакетов C++ для Windows](/cpp/vcpkg), чтобы установить диспетчер vcpkg (если у вас его еще нет).

1. Установка динамической или статической библиотеки Boost.Test:

    - Запустите `vcpkg install boost-test`, чтобы установить динамическую библиотеку Boost.Test.
    
       -ИЛИ-
       
    - Запустите `vcpkg install boost-test:x86-windows-static`, чтобы установить статическую библиотеку Boost.Test.

1. Выполните `vcpkg integrate install`, чтобы настроить в Visual Studio библиотеку и пути включения для заголовков и двоичных файлов Boost.

## <a name="create-a-project-for-your-tests"></a>Создание проекта для тестов

> [!NOTE]
> В Visual Studio 2017 версии 15.5 для Boost.Test нет предварительно настроенного тестового проекта или шаблонов элементов. Поэтому необходимо создать проект консольного приложения, в котором будут помещаться тесты. Шаблоны тестов для Boost.Test планируется включить в будущей версии Visual Studio.

1. В **обозревателе решений** щелкните узел решения правой кнопкой мыши и выберите пункты **Добавить** > **Новый проект**.

1. В левой области выберите **Visual C++** > **Рабочий стол Windows**, а затем выберите шаблон **Консольное приложение Windows**.

1. Присвойте проекту имя и нажмите кнопку **ОК**.

## <a name="link-and-configuration-boost-static-library-only"></a>Ссылки и конфигурации (только для статической библиотеки Boost)

Настройте проект для выполнения тестов Boost.Test.

1. Чтобы изменить файл проекта, сначала выгрузите его. В **обозревателе решений** щелкните узел проекта правой кнопкой мыши и выберите пункт **Выгрузить проект**. Затем щелкните правой кнопкой мыши узел проекта и выберите **Изменить <имя\>.vcxproj**.

1. Добавьте две строки в группу свойств **Глобальные**, как показано ниже:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Сохраните и закройте \*VCXPROJ-файл и затем перезагрузите проект.

1. Чтобы открыть диалоговое окно **Страницы свойств**, щелкните узел проекта правой кнопкой мыши и выберите пункт **Свойства**.

1. Разверните узел **C/C++** > **Создание кода**, а затем выберите элемент **Библиотека времени выполнения**. Выберите `/MTd` для статической библиотеки времени выполнения отладки или `/MT` для статической библиотеки времени выполнения выпуска.

1. Разверните узел **Компоновщик > Система**. Убедитесь, что параметру **SubSystem** задано значение **Консоль**.

1. Нажмите кнопку **ОК**, чтобы закрыть окно страниц свойств.

## <a name="add-include-directives"></a>Добавление директив include

1. Если в CPP-файле теста имеется функция `main`, удалите ее.

1. В CPP-файле теста добавьте необходимые директивы `#include`, чтобы типы и функции программы были доступны коду теста. Как правило, программа находится в иерархии папок на один уровень выше. При вводе `#include "../"` открывается окно IntelliSense, в котором можно выбрать полный путь к файлу заголовка.

   ![Добавление директив #include](media/cpp-gtest-includes.png "Добавление директив include в CPP-файл теста")

   Можно использовать автономную библиотеку с:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Или использовать версию с одним заголовком с:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Затем определите `BOOST_TEST_MODULE`.

Приведенного ниже примера достаточно для обнаружения теста в **обозревателе тестов**.

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Написание и запуск тестов
Все готово к написанию и выполнению тестов Boost Test. Сведения о макросах тестов см. в [документации по библиотеке Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Сведения об обнаружении, выполнении и группировании тестов с помощью **обозревателя тестов** см. в статье [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>См. также
[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)
