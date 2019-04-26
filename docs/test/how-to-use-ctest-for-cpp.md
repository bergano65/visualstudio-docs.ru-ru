---
title: Использование CTest для C++
ms.date: 11/07/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6be079a5adfe52a7ac750f6713672dad50c7d2a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945388"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Использование CTest для C++ в Visual Studio

Система CMake (которая включает в себя CTest) по умолчанию интегрирована в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Если вам нужно установить этот компонент на компьютере, откройте программу Visual Studio Installer, нажмите кнопку **Изменить** и установите флажок [Инструменты Visual C++ для CMake](/cpp/ide/cmake-tools-for-visual-cpp) в списке компонентов рабочей нагрузки.

## <a name="to-write-tests"></a>Написание тестов

Поддержка CMake в Visual Studio не распространяется на систему проектов Visual Studio. Поэтому тесты CTest создаются и настраиваются так же, как в любой среде CMake. Дополнительные сведения об использовании CMake в Visual Studio см. в статье об [инструментах CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests"></a>Выполнение тестов

::: moniker range="vs-2017"

### <a name="visual-studio-2017-version-156-and-later"></a>Visual Studio 2017 версии 15.6 и более поздней

В Visual Studio 2017 версии 15.6 и более поздней инструмент CTest полностью интегрирован с **обозревателем тестов** и поддерживает платформы модульного тестирования Google и Boost. Эти платформы по умолчанию включены в качестве компонентов рабочей нагрузки **Разработка классических приложений на C++**. Но если вы обновляете проект с более старой версии Visual Studio, может потребоваться установить эти платформы с помощью программы Visual Studio Installer.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![Выполнение CTest с помощью платформы Google Test в Visual Studio 2017](media/ctest-test-explorer.png)

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 версии 15.5

В Visual Studio 2017 версии 15.5 инструмент CTest не интегрируется с **обозревателем тестов**. Вы можете выполнять тесты из главного меню CMake или контекстного меню файла *CMakeLists.txt* в **обозревателе решений**. Результаты тестов направляются в **окно вывода** Visual Studio.

![Выполнение CTest в Visual Studio 2017 версии 15.5](media/cpp-cmake-run-tests.png)

::: moniker-end

::: moniker range=">=vs-2019"

CTest полностью интегрирован с **обозревателем тестов** и поддерживает платформы модульного тестирования Google и Boost. Эти платформы по умолчанию включены в качестве компонентов рабочей нагрузки **Разработка классических приложений на C++**. Но если вы обновляете проект с более старой версии Visual Studio, может потребоваться установить эти платформы с помощью программы Visual Studio Installer.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![Выполнение CTest с помощью платформы Google Test в Visual Studio](media/ctest-test-explorer.png)

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

::: moniker-end

## <a name="see-also"></a>См. также

- [Написание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)