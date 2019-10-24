---
title: Подготовка к отладке C++ проектов | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9c7d223b9ea542177176045c9abd103958e5ae33
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738113"
---
# <a name="debugging-preparation-c-project-types"></a>Подготовка к отладке: C++ типы проектов
В этом разделе описана отладка основных типов проектов, созданных с использованием шаблонов проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].

 Обратите внимание, что типы проектов, которые создают библиотеки DLL в качестве выходных данных, были сгруппированы в [отладочные проекты](../debugger/debugging-dll-projects.md) , так как они являются общими функциями, к которым они относятся.

## <a name="BKMK_In_this_topic"></a> Содержание раздела
 [Рекомендуемые значения свойств](#BKMK_Recommended_Property_Settings)

 [Проекты Win32](#BKMK_Win32_Projects)

- [Отладка приложения Win32 на C или C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Ручная установка конфигурации отладки](#BKMK_To_manually_set_a_Debug_configuration)

  [Приложения Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a> Рекомендуемые значения свойств
 Некоторые свойства должны быть установлены одинаково для всех скриптов неуправляемой отладки. В следующих таблицах приводятся рекомендованные параметры свойств. Параметры, здесь не перечисленные, могут иметь различные значения для различных типов неуправляемых проектов. Дополнительные сведения см. [в C++ разделе Параметры проекта для конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Узел " &#124; свойства конфигурацииC++ &#124; C/оптимизация"

|Имя свойства|Параметр|
|-------------------|-------------|
|**Optimization**|Установите значение **Отключено (/0d)** . Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне **Дизассемблированный код**, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Другие возможности, такие как пошаговое выполнение, могут действовать не так, как ожидалось.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Узел &#124; отладки &#124; свойств конфигурации компоновщик

|Имя свойства|Параметр|
|-------------------|-------------|
|**Создать отладочную информацию**|Следует всегда устанавливать этот параметр в **Да (/DEBUG)** для создания символов отладки и необходимых для нее файлов. Когда приложение выходит в производство, этот параметр можно отключить.|

 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a> Проекты Win32
 Win32-приложения — это традиционные программы для Windows, написанные на C или C++. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений.

 Win32-приложения включают приложения MFC и ATL-проекты. В них используются Windows API и могут использоваться MFC или ATL, но они не используют среду CLR. Они могут, однако, вызывать управляемый код, использующий среду CLR.

 В следующей процедуре описывается отладка проекта Win32 в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Еще одним способом отладки приложений Win32 является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. [в разделе Присоединение к запущенным процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Отладка приложения Win32 на C или C++

1. Откройте проект в Visual Studio.

2. В меню **Отладка** выберите команду **Пуск**.

3. Отладка с использованием методик, обсуждаемых в [первом взгляде на отладчик](../debugger/debugger-feature-tour.md).

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Ручная установка конфигурации отладки

1. В меню **Вид** выберите команду **Страницы свойств**.

2. Щелкните узел **Свойства конфигурации**, чтобы раскрыть его, если он еще не раскрыт.

3. Выберите **Общие** и установите для строки **Вывод** значение **Отладка**.

4. Откройте узел **С/С++** и выберите пункт **Общие**.

    В строке **Отладка** можно указать тип отладочной информации, которая будет создана компилятором. Можно выбрать **База данных программы (/Zi)** или **База данных программы для операции "Изменить и продолжить" (/ZI)** .

5. Выберите **Оптимизация** и в строке **Оптимизация** выберите пункт **Отключена (/0D)** в раскрывающемся списке.

    Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне Дизассемблированный код, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Такие возможности, как пошаговое выполнение, скорее всего будут неправильно показывать точки останова и точки выполнения.

6. Откройте узел **Компоновщик** и выберите **Отладка**. В первой строке **Создать** выберите параметр **Да (/DEBUG)** из раскрывающегося списка. Всегда делайте так при отладке.

   Дополнительные сведения см.[в C++ разделе Параметры проекта для конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a> Приложения Windows Forms (.NET)
 Шаблон **Приложение Windows Forms (.NET)** создает приложение Windows Forms [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Для получения дополнительной информации см. [How to: Create a Windows Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] аналогична отладке управляемых приложений Windows Forms.

 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. Если необходимо, эти параметры можно изменить в диалоговом окне **\<имя проекта> Страницы свойств**. Дополнительные сведения см. в разделе [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).

 Дополнительные сведения см. [в C++ разделе Параметры проекта для конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Еще одним способом отладки приложений Windows Forms является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [Подключение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>См. также
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Подключение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)
- [Практическое руководство. Создание проекта приложения Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))