---
title: Запуск приложений Магазина Windows на локальном компьютере | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196331"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Запуск приложений для Магазина Windows на локальном компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется только к Windows] (.. /Video windows_only_content.png "windows_only_content")  
  
 Чтобы провести отладку, тестирование или анализ производительности для приложения Магазина Windows, вы можете запустить это приложение на том же компьютере, где размещается Visual Studio. Если экран устройства поддерживает сенсорное управление, вам становятся доступны все функции приложения, в противном случае вы сможете использовать только жесты, выполняемые с помощью мыши и клавиатуры.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Содержание раздела  
 В разделе содержится следующая информация:  
  
 [Запуск на локальном компьютере](#BKMK_How_to_run_on_a_local_machine)  
  
 [Переключение между приложением Магазина Windows и Visual Studio на одном мониторе](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Запуск на локальном компьютере  
 Чтобы запустить приложение на локальном компьютере, выберите **локальный компьютер** в раскрывающемся списке рядом с кнопкой начать отладку на **стандартной** панели инструментов отладчика.  
  
 ![Запуск на локальном компьютере](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Если панель инструментов **Стандартная** не отображается, в меню **вид** выберите пункт **панели инструментов**, а затем пункт **стандартный**.  
  
 Выбор, производимый в раскрывающемся списке, сохраняется в файле свойств проекта и используется для запуска по умолчанию.  
  
 Целевой объект запуска также можно задать напрямую в файле свойств проекта. Щелкните правой кнопкой мыши имя проекта в **Обозреватель решений** а затем выберите пункт **свойства**. Выполните одно из следующих действий.  
  
- В проектах C# и Visual Basic щелкните **Отладка** , а затем выберите **локальный компьютер** в раскрывающемся списке **целевое устройство** .  
  
     ![Страница свойств&#35; и Visual Basic проекта в C](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- В проектах C++ и JavaScript разверните узел **Свойства конфигурации** , щелкните **Отладка**, а затем выберите **локальный отладчик** из списка **отладчик для запуска** .  
  
     ![Страница свойств&#43;&#43; и проекта JavaScript в C](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Переключение между приложением Магазина Windows и Visual Studio на одном мониторе  
 **Порядок переключения из выполняемого экземпляра приложения Магазина Windows в Visual Studio**  
  
 Если вы запускаете приложение Магазина Windows на локальном компьютере и используете один монитор, вам может потребоваться вернуться в Visual Studio, оставив приложение выполняющимся. Например, приложение может находиться в состоянии, которого нельзя добиться с помощью точки останова, например, ожидать события или выполняться в длительном или бесконечном цикле. Чтобы вернуться в Visual Studio, нажмите ALT+TAB.
