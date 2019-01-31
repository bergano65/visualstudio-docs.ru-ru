---
title: Подготовка к отладке проектов C++ | Документация Майкрософт
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
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 223a04eada43d9ca69bf5f2d6b5a36ce2d7a5933
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979170"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Подготовка к отладке: Типы проектов Visual C++
В этом разделе описана отладка основных типов проектов, созданных с использованием шаблонов проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Обратите внимание, что эти типы проектов, которые создают DLL свои выходные данные были сгруппированы в [отладка проектов DLL](../debugger/debugging-dll-projects.md) из-за их общих особенностей.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Рекомендуемые значения свойств](#BKMK_Recommended_Property_Settings)  
  
 [Проекты Win32](#BKMK_Win32_Projects)  
  
- [Отладка приложения Win32 на C или C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Ручная установка конфигурации отладки](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Приложения Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Рекомендуемые значения свойств  
 Некоторые свойства должны быть установлены одинаково для всех скриптов неуправляемой отладки. В следующих таблицах приводятся рекомендованные параметры свойств. Параметры, здесь не перечисленные, могут иметь различные значения для различных типов неуправляемых проектов. Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Свойства конфигурации &#124; C/C++ &#124; узел оптимизации  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Optimization**|Установите значение **Отключено (/0d)**. Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне **Дизассемблированный код**, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Другие возможности, такие как пошаговое выполнение, могут действовать не так, как ожидалось.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Свойства конфигурации &#124; компоновщика &#124; Отладка  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Создать отладочную информацию**|Следует всегда устанавливать этот параметр в **Да (/DEBUG)** для создания символов отладки и необходимых для нее файлов. Когда приложение выходит в производство, этот параметр можно отключить.|  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Проекты Win32  
 Win32-приложения — это традиционные программы для Windows, написанные на C или C++. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений.  
  
 Win32-приложения включают приложения MFC и ATL-проекты. В них используются Windows API и могут использоваться MFC или ATL, но они не используют среду CLR. Они могут, однако, вызывать управляемый код, использующий среду CLR.  
  
 В следующей процедуре описывается отладка проекта Win32 в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Еще одним способом отладки приложений Win32 является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Отладка приложения Win32 на C или C++  
  
1.  Откройте проект в Visual Studio.  
  
2.  В меню **Отладка** выберите команду **Пуск**.  
  
3.  Отладка использует методы, обсуждаемые в [сначала посмотрим, отладчик](../debugger/debugger-feature-tour.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Ручная установка конфигурации отладки  
  
1. В меню **Вид** выберите команду **Страницы свойств**.  
  
2. Щелкните узел **Свойства конфигурации**, чтобы раскрыть его, если он еще не раскрыт.  
  
3. Выберите **Общие** и установите для строки **Вывод** значение **Отладка**.  
  
4. Откройте узел **С/С++** и выберите пункт **Общие**.  
  
    В строке **Отладка** можно указать тип отладочной информации, которая будет создана компилятором. Можно выбрать **База данных программы (/Zi)** или **База данных программы для операции "Изменить и продолжить" (/ZI)**.  
  
5. Выберите **Оптимизация** и в строке **Оптимизация** выберите пункт **Отключена (/0D)** в раскрывающемся списке.  
  
    Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне Дизассемблированный код, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Такие возможности, как пошаговое выполнение, скорее всего будут неправильно показывать точки останова и точки выполнения.  
  
6. Откройте узел **Компоновщик** и выберите **Отладка**. В первой строке **Создать** выберите параметр **Да (/DEBUG)** из раскрывающегося списка. Всегда делайте так при отладке.  
  
   Дополнительные сведения см. в разделе[параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Приложения Windows Forms (.NET)  
 Шаблон **Приложение Windows Forms (.NET)** создает приложение Windows Forms [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Дополнительные сведения см. в разделе [Как создать проект приложения Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).  
  
 Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] аналогична отладке управляемых приложений Windows Forms.  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. Если необходимо, эти параметры можно изменить в диалоговом окне **\<имя проекта> Страницы свойств**. Дополнительные сведения см. в разделе [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Еще одним способом отладки приложений Windows Forms является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [Подключение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>См. также раздел  
 [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Подключение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Практическое руководство. Создание проекта приложения Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))