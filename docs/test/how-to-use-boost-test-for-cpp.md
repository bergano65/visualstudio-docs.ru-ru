---
title: "Использование Boost.Test для C++ в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af55f9f124b2ec609c4f0a590e7c2fab738624d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Использование Boost.Test для C++ в Visual Studio
В **Visual Studio 2017 версии 15.5** и более поздних Boost.Test интегрирован в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Чтобы установить этот компонент на компьютере, откройте Visual Studio Installer и найдите пункт **Адаптер Boost.Test** в списке компонентов рабочей нагрузки.

![Установка Boost Test](media/cpp-boost-component.png "Установка Boost.Test для C++")

## <a name="install-boost"></a>Установка Boost

 Для Boost.Test требуется [Boost](http://www.boost.org/). Если у вас не установлен Boost, рекомендуем воспользоваться диспетчером пакетов Vcpkg. 

1. Следуйте инструкциям в статье [vcpkg: диспетчер пакетов C++ для Windows](/cpp/vcpkg), чтобы установить диспетчер vcpkg (если у вас его еще нет).
2. Чтобы установить библиотеки Boost, выполните команду `vcpkg install boost`.
3. Выполните команду `vcpkg integrate install`, чтобы настроить в Visual Studio библиотеку и пути включения для заголовков и двоичных файлов Boost. 

## <a name="create-a-project-for-your-tests"></a>Создание проекта для тестов
В Visual Studio 2017 версии 15.5 для Boost.Test нет предварительно настроенного тестового проекта или шаблонов элементов. Поэтому необходимо создать проект консольного приложения, в котором будут помещаться тесты. Шаблоны тестов для Boost.Test планируется включить в будущей версии Visual Studio. 

1. В **обозревателе решений** щелкните узел решения правой кнопкой мыши и выберите пункты **Добавить | Новый проект**. 
2. В левой области выберите **Рабочий стол Windows**, а в центральной области выберите тип проекта **Консольное приложение Windows**. 
3. Укажите имя проекта и нажмите кнопку **ОК**. 

## <a name="add-include-directives"></a>Добавление директив include
В CPP-файле теста добавьте необходимые директивы `#include`, чтобы типы и функции программы были доступны коду теста. Как правило, программа находится в иерархии папок на один уровень выше. Если ввести `#include "../"`, появится окно IntelliSense, в котором можно выбрать полный путь к файлу заголовка.

![Добавление директив #include](media/cpp-gtest-includes.png "Добавление директив include в CPP-файл теста")

Необходимо включить по крайней мере [один вариант заголовка для Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) с `#include <path>/unit_test.hpp` и определить `BOOST_TEST_MODULE`. Приведенного ниже примера достаточно для обнаружения теста в **обозревателе тестов**.

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Написание и запуск тестов
Все готово к написанию и выполнению тестов Boost Test. Сведения о макросах тестов см. в [документации по библиотеке Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Сведения об обнаружении, выполнении и группировании тестов с помощью **обозревателя тестов** см. в статье [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>См. также
[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)


  







