---
title: Использование CTest для C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: fddb32ce75bf587ee78ca172fd4de2c31237a331
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225938"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Использование CTest для C++ в Visual Studio 2017 и более поздних версиях

Система CMake (которая включает в себя CTest) по умолчанию интегрирована в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Если вам нужно установить ее на компьютере, откройте программу Visual Studio Installer, нажмите кнопку **Разработка классических приложений на C++** , а затем выберите команду **Изменить**. Установите флажок [Инструменты CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) в списке компонентов рабочей нагрузки.

## <a name="to-write-tests"></a>Написание тестов

Поддержка CMake в Visual Studio не распространяется на систему проектов Visual Studio. Поэтому тесты CTest создаются и настраиваются так же, как в любой среде CMake. Дополнительные сведения об использовании CMake в Visual Studio см. в статье об [инструментах CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests"></a>Выполнение тестов

CTest полностью интегрирован с **обозревателем тестов** и поддерживает платформы модульного тестирования Google и Boost. Эти платформы по умолчанию включены в качестве компонентов рабочей нагрузки **Разработка классических приложений на C++**. Но если вы обновляете проект с более старой версии Visual Studio, может потребоваться установить эти платформы с помощью программы Visual Studio Installer.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![Выполнение CTest с помощью платформы Google Test в Visual Studio](media/ctest-test-explorer.png)

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

На следующем рисунке показаны результаты выполнения CTest с использованием платформы Google Test.

![Выполнение CTest с помощью платформы Google Test в Visual Studio 2017](media/ctest-test-explorer.png)

Если вы используете CTest, но не используете адаптеры Google или Boost, результаты будут доступны на уровне CTest, а не на отдельном уровне метода проверки. Вы сможете выполнять отладку и использовать пошаговый режим для исполняемых файлов CTest, но без трассировки стека для отдельных тестов.

## <a name="see-also"></a>См. также

- [Написание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)