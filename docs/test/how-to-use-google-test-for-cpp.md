---
title: Использование Google Test для C++ в Visual Studio | Документы Майкрософт
ms.date: 11/04/2017
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: d525a9aae0f376ada2cbb48b2ac07acbb21f436c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Использование Google Test для C++ в Visual Studio
В **Visual Studio 2017 версии 15.5** и более поздних Google Test интегрирован в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Чтобы проверить, установлен ли этот компонент на компьютере, откройте Visual Studio Installer и найдите Google Test в списке компонентов рабочей нагрузки.

![Установка Google Test](media/cpp-google-component.png "Установка Google Test для C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Добавление проекта Google Test в решение
1. В **обозревателе решений** щелкните узел решения правой кнопкой мыши и выберите пункты **Добавить | Новый проект**.
2. В левой области выберите **Visual C++ | Тест**, а в центральной области выберите один тип проекта **Проект Google Test**.
3. Укажите имя тестового проекта и нажмите кнопку **ОК**.

![Новый проект Google Test](media/cpp-gtest-new-project.png "Добавление нового проекта Google Test")

## <a name="configure-the-test-project"></a>Настройка тестового проекта
В открывшемся диалоговом окне **Конфигурация тестового проекта** можно выбрать проект, который необходимо тестировать. При выборе проекта Visual Studio добавляет ссылку на него. Если проект не выбран, необходимо вручную добавить ссылки на проекты, которые следует тестировать. При выборе статического или динамического связывания с двоичными файлами Google Test следует учитывать те же факторы, что и в случае с любой другой программой C++. Дополнительные сведения см. в статье [DLL в Visual C++](/cpp/build/dlls-in-visual-cpp).

 ![Настройка проекта Google Test](media/cpp-gtest-config.png "Настройка проекта Google Test")

## <a name="set-additional-options"></a>Настройка дополнительных параметров
Чтобы настроить дополнительные параметры, в главном меню выберите **Сервис | Параметры | Адаптер тестов для Google Test**. Дополнительные сведения об этих параметрах см. в документации по Google Test.

 ![Параметры проекта Google Test](media/cpp-gtest-settings.png "Параметры проекта Google Test")

## <a name="add-include-directives"></a>Добавление директив include
В CPP-файле теста добавьте необходимые директивы `#include`, чтобы типы и функции программы были доступны коду теста. Как правило, программа находится в иерархии папок на один уровень выше. Если ввести `#include "../"`, появится окно IntelliSense, в котором можно выбрать полный путь к файлу заголовка.

![Добавление директив #include](media/cpp-gtest-includes.png "Добавление директив include в CPP-файл теста")

## <a name="write-and-run-tests"></a>Написание и запуск тестов
Все готово к написанию и выполнению тестов Google Test. Сведения о макросах тестов см. в [учебнике по началу работы с Google Test](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md). Сведения об обнаружении, выполнении и группировании тестов с помощью **обозревателя тестов** см. в статье [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>См. также
[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)










