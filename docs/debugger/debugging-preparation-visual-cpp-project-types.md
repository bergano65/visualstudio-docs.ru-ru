---
title: 'Подготовка к отладке: Типы проектов Visual C++ | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: e02be24447d5383388be0a7208bf84e36333732f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-preparation-visual-c-project-types"></a>Подготовка к отладке: типы проектов Visual C++
В этом разделе описана отладка основных типов проектов, созданных с использованием шаблонов проектов [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Обратите внимание, что эти типы проектов, которые создают DLL свои выходные данные были сгруппированы в [отладки проектов DLL](../debugger/debugging-dll-projects.md) из-за их общих особенностей.  
  
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
|**Optimization**|Значение **отключено (/ 0 d).** Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, можно включить этот параметр, но помните, что код, показываемый в **Дизассемблирование** генерируется из оптимизированного источника и может не совпадать с вы видите в источнике Windows. Другие возможности, такие как пошаговое выполнение, могут действовать не так, как ожидалось.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Свойства конфигурации &#124; компоновщика &#124; Отладка  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Создать отладочную информацию**|Следует всегда устанавливать этот параметр в **Да (/ DEBUG)** для создания символов отладки и необходимых для неё файлов. Когда приложение выходит в производство, этот параметр можно отключить.|  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Проекты Win32  
 Win32-приложения — это традиционные программы для Windows, написанные на C или C++. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений.  
  
 Win32-приложения включают приложения MFC и ATL-проекты. В них используются Windows API и могут использоваться MFC или ATL, но они не используют среду CLR. Они могут, однако, вызывать управляемый код, использующий среду CLR.  
  
 В следующей процедуре описывается отладка проекта Win32 в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Еще одним способом отладки приложений Win32 является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [присоединение к процессу под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Для отладки приложения на C или C++ Win32  
  
1.  Откройте проект в Visual Studio.  
  
2.  На **отладки** меню, выберите **запустить**.  
  
3.  Отладка с помощью способов, приведенных в [основы отладчик](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Ручная установка конфигурации отладки  
  
1.  На **представление** меню, нажмите кнопку **страницы свойств**.  
  
2.  Нажмите кнопку **свойства конфигурации** узел, чтобы открыть его, если он еще не  
  
3.  Выберите **Общие**и установите для параметра **вывода** строки **отладки**.  
  
4.  Откройте **C/C++** , а затем установите **Общие**.  
  
     В **отладки** строк, можно указать тип отладочной информации, создаваемой компилятором. Можно выбрать значения включают **базы данных программы (/Zi)** или **база данных программы для изменить и продолжить "(/ZI)**.  
  
5.  Выберите **оптимизации**и в **оптимизации** строк, выберите **отключено (/ 0d)** из раскрывающегося списка.  
  
     Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне Дизассемблированный код, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Такие возможности, как пошаговое выполнение, скорее всего будут неправильно показывать точки останова и точки выполнения.  
  
6.  Откройте **компоновщика** , а затем установите **Отладка**. В первом **формирования** строк, выберите **Да (/ DEBUG)** из раскрывающегося списка. Всегда делайте так при отладке.  
  
 Дополнительные сведения см. в разделе[параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Приложения Windows Forms (.NET)  
 **Приложение Windows Forms (.NET)** шаблон создает [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] приложение Windows Forms. Для получения дополнительной информации см. [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] аналогична отладке управляемых приложений Windows Forms.  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости можно изменить эти параметры в  **\<имя проекта > страницы свойств** диалоговое окно. Дополнительные сведения см. в разделе [конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Еще одним способом отладки приложений Windows Forms является запуск приложения вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [присоединение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/debugger-basics.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Присоединение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Как: Создание проекта приложения Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)