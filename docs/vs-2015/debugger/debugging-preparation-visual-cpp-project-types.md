---
title: 'Подготовка к отладке: Типы проектов Visual C++ | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 592232277dd8eda337bf90e6df114c2a03e75c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562652"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Подготовка к отладке: типы проектов Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Подготовка к отладке: типы проектов Visual C++](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-visual-cpp-project-types).  
  
В этом разделе описана отладка основных типов проектов, созданных с использованием шаблонов проектов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
 Обратите внимание, что эти типы проектов, которые создают DLL свои выходные данные были сгруппированы в [отладка проектов DLL](../debugger/debugging-dll-projects.md) из-за их общих особенностей.  
  
##  <a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Рекомендуемые параметры свойств](#BKMK_Recommended_Property_Settings)  
  
 [Проекты Win32](#BKMK_Win32_Projects)  
  
-   [Для отладки приложения на C или C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Ручная установка конфигурации отладки](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Приложения Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Рекомендуемые параметры свойств  
 Некоторые свойства должны быть установлены одинаково для всех скриптов неуправляемой отладки. В следующих таблицах приводятся рекомендованные параметры свойств. Параметры, здесь не перечисленные, могут иметь различные значения для различных типов неуправляемых проектов. Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Свойства конфигурации &#124; C/C++ &#124; узел оптимизации  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Optimization**|Значение **отключено (/ 0 d).** Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если вы в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, можно включить этот параметр, но помните, что код, показанный на **Дизассемблированный код** окна формируется из оптимизированного источника и может не совпадать с вы видите в источнике Windows. Другие возможности, такие как пошаговое выполнение, могут действовать не так, как ожидалось.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Свойства конфигурации &#124; компоновщика &#124; Отладка  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Создает отладочную информацию**|Следует всегда устанавливать этот параметр, **Да (/ DEBUG)** для создания символов отладки и файлы, необходимые для отладки. Когда приложение выходит в производство, этот параметр можно отключить.|  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Проекты Win32  
 Win32-приложения — это традиционные программы для Windows, написанные на C или C++. Отладка приложений такого типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не вызывает никаких затруднений.  
  
 Win32-приложения включают приложения MFC и ATL-проекты. В них используются Windows API и могут использоваться MFC или ATL, но они не используют среду CLR. Они могут, однако, вызывать управляемый код, использующий среду CLR.  
  
 В следующей процедуре описывается отладка проекта Win32 в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Еще одним способом отладки приложений Win32 является запуск приложения вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Для отладки приложения на C или C++ Win32  
  
1.  Откройте проект в Visual Studio.  
  
2.  На **Отладка** меню, выберите **запустить**.  
  
3.  Отладка использует методы, обсуждаемые в [Общие сведения об отладчике](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Ручная установка конфигурации отладки  
  
1.  На **представление** меню, щелкните **страницы свойств**.  
  
2.  Нажмите кнопку **свойства конфигурации** узел, чтобы открыть его, если это еще не сделано  
  
3.  Выберите **Общие**и установите для параметра **вывода** строки **Отладка**.  
  
4.  Откройте **C/C++** узел и выберите **Общие**.  
  
     В **Отладка** строк указать тип отладочной информации, создаваемого компилятором. Можно выбрать значения включают **база данных программы (/Zi)** или **база данных программы для изменить и продолжить "(/ZI)**.  
  
5.  Выберите **оптимизации**и в **оптимизации** строку, выберите **отключено (/ 0d)** из раскрывающегося списка.  
  
     Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне Дизассемблированный код, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Такие возможности, как пошаговое выполнение, скорее всего будут неправильно показывать точки останова и точки выполнения.  
  
6.  Откройте **компоновщика** узел и выберите **Отладка**. В первом **формирования** строку, выберите **Да (/ DEBUG)** из раскрывающегося списка. Всегда делайте так при отладке.  
  
 Дополнительные сведения см. в разделе[параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Приложения Windows Forms (.NET)  
 **Приложение Windows Forms (.NET)** шаблон создает [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] приложение Windows Forms. Для получения дополнительной информации см. [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Отладка приложений такого типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] аналогична отладке управляемых приложений Windows Forms.  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости вы можете изменить эти параметры в  **\<имя проекта > страницы свойств** диалоговое окно. Дополнительные сведения см. в разделе [конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Еще одним способом отладки приложений Windows Forms является запуск приложения вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [присоединение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/debugger-basics.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Присоединение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Практическое: Создание проекта приложения Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)



