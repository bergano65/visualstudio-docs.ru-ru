---
title: Использование CTest для C++ в Visual Studio
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 98e258c2547bbd3cd1b87d289bf643956acfdb1d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751037"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Использование CTest для C++ в Visual Studio

Система CMake (которая включает в себя CTest) по умолчанию интегрирована в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Если вам нужно установить этот компонент на компьютере, откройте программу Visual Studio Installer, нажмите кнопку **Изменить** и установите флажок [Инструменты Visual C++ для CMake](/cpp/ide/cmake-tools-for-visual-cpp) в списке компонентов рабочей нагрузки.

## <a name="to-write-tests"></a>Написание тестов

Поддержка CMake в Visual Studio не распространяется на систему проектов Visual Studio. Поэтому тесты CTest создаются и настраиваются так же, как в любой среде CMake. Дополнительные сведения об использовании CMake в Visual Studio см. в статье об [инструментах CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Выполнение тестов (Visual Studio 2017 версии 15.6)

В Visual Studio 2017 версии 15.6 инструмент CTest полностью интегрирован с **обозревателем тестов** и поддерживает платформы модульного тестирования Google и Boost. Эти платформы по умолчанию включены в качестве компонентов рабочей нагрузки **Разработка классических приложений на C++**. Но если вы обновляете проект с более старой версии Visual Studio, может потребоваться установить эти платформы с помощью программы Visual Studio Installer.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![Выполнение CTest с помощью платформы Google Test в VS2017 15.6](media/ctest-test-explorer.png)

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Выполнение тестов (Visual Studio 2017 версии 15.5)

В **Visual Studio 2017 версии 15.5** инструмент CTest не интегрируется с **обозревателем тестов**. Вы можете выполнять тесты из главного меню CMake или из контекстного меню файла **CMakeLists.txt** в **обозревателе решений**. Результаты тестов направляются в **окно вывода** Visual Studio.

![Выполнение тестов CTest в VS2017 15.5](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>См. также

[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)