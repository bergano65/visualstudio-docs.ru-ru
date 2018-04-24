---
title: Использование CTest для C++ в Visual Studio | Документы Майкрософт
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 5956c605eb838721185598d4c5713c59164db071
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Использование CTest для C++ в Visual Studio

Система CMake (которая включает в себя CTest) по умолчанию интегрирована в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Если вам нужно установить этот компонент на компьютере, откройте программу Visual Studio Installer, нажмите кнопку **Изменить** и установите флажок [Инструменты Visual C++ для CMake](/cpp/ide/cmake-tools-for-visual-cpp) в списке компонентов рабочей нагрузки.

## <a name="to-write-tests"></a>Написание тестов

Поддержка CMake в Visual Studio не распространяется на систему проектов Visual Studio. Поэтому тесты CTest создаются и настраиваются так же, как в любой среде CMake. Дополнительные сведения об использовании CMake в Visual Studio см. в статье об [инструментах CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Выполнение тестов (Visual Studio 2017 версии 15.6)

В Visual Studio 2017 версии 15.6 инструмент CTest полностью интегрирован с **обозревателем тестов** и поддерживает платформы модульного тестирования Google и Boost. Эти платформы по умолчанию включены в качестве компонентов рабочей нагрузки **Разработка классических приложений на C++**. Но если вы обновляете проект с более старой версии Visual Studio, может потребоваться установить эти платформы с помощью программы Visual Studio Installer.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![CTest и платформа Google Test в VS 2017 версии 15.6](media/ctest-test-explorer.png "CTest and Google Test in Test Explorer")

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Выполнение тестов (Visual Studio 2017 версии 15.5)

В **Visual Studio 2017 версии 15.5** инструмент CTest не интегрируется с **обозревателем тестов**. Вы можете выполнять тесты из главного меню CMake или из контекстного меню файла **CMakeLists.txt** в **обозревателе решений**. Результаты тестов направляются в **окно вывода** Visual Studio.

![Выполнение тестов CTest в VS 2017 15.5](media/cpp-cmake-run-tests.png "Run CTest tests in 15.5")

## <a name="see-also"></a>См. также

[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)