---
title: Отладка проектов DLL | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb1d8cf355aee56797b5c814341255cb47cf4f9b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267388"
---
# <a name="debugging-dll-projects"></a>Отладка проектов DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Следующие шаблоны создают DLL:  
  
-   Библиотека классов (C++, C# и Visual Basic)  
  
-   (C++, C# и Visual Basic): Библиотека элементов управления Windows Forms  
  
     Отладка библиотеки элементов управления Windows аналогична отладке проекта библиотеки классов. В большинстве случаев элемент управления Windows вызывается из другого проекта. При отладке вызывающего проекта можно осуществлять пошаговое выполнение элемента управления Windows, устанавливать точки останова и выполнять другие операции отладки. Дополнительные сведения см. в разделе [Элементы управления Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
-   (C# и Visual Basic): библиотека элементов управления веб  
  
     Для получения дополнительной информации см. [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md).  
  
-   (C++): Элементы управления ActiveX и Smart Device ActiveX библиотеки MFC  
  
     Элементы управления ActiveX — это элементы управления, которые могут быть загружены через Интернет на компьютер клиента, а затем отображены и активированы на веб–страницах.  
  
     Отладка элементов управления ActiveX аналогична отладке других типов элементов управления, поскольку они не могут быть запущены сами по себе, а должны быть внедрены в веб–страницу HTML. Дополнительные сведения см. в разделе [How to: Debug an ActiveX Control](../debugger/how-to-debug-an-activex-control.md).  
  
-   (C++): MFC Smart Device DLL  
  
     Дополнительные сведения см. в разделе [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).  
  
 В этом разделе также содержатся сведения по следующим темам:  
  
-   [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)  
  
-   [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)  
  
 В этом разделе содержатся следующие подразделы, относящиеся к подготовке отладки библиотек классов:  
  
-   [Building a Debug Version](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
-   [Mixed-Mode Debugging](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
-   [Changing Default Configurations](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
-   [Ways to Debug the DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
-   [The Calling Application](#vxtskdebuggingdllprojectsthecallingapplication)  
  
-   [Controls on a Web Page](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
-   [The Immediate Window](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a Debug Version  
 Независимо от того, как выполняется отладка, сначала убедитесь, что собрана отладочная версия DLL, и что эта версия находится в том месте, в котором приложение и ожидает ее найти. Это может казаться очевидным, но если этот этап будет пропущен, приложение может найти другую версию этой DLL и загрузить ее. После этого программа продолжит выполнение, а вы будете удивляться, почему выполнение ни разу не прервалось на точке останова. В процессе отладки можно проверить, какую DLL загрузила программа, открыв в отладчике окно **Модули** . В окне **Модули** имеется список всех DLL или исполняемых файлов, загруженных в отлаживаемый процесс. Для получения дополнительной информации см. [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
  
 Чтобы отладчик мог присоединиться к коду на языке C++, код должен иметь `DebuggableAttribute`. Это можно добавить в код автоматически, путем связывания с параметром [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) компоновщика.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode Debugging  
 Вызывающее DLL приложение может быть написано как в управляемом, так и в машинном коде. Если управляемая DLL вызывается машинным кодом, а надо отлаживать обе части кода, то оба отладчика — управляемый и машинный — должны быть включены. Это можно сделать в  **\<проект > страницы свойств** диалогового окна или окна. Способ выполнения этой операции зависит от того, откуда была запущена отладка: из проекта DLL или из проекта вызывающего приложения. Дополнительные сведения см. в разделе [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing Default Configurations  
 При создании проекта консольного приложения с использованием шаблона проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически устанавливает необходимые параметры для отладочной и окончательной конфигурации. При необходимости эти параметры можно изменить. Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [параметры проекта для конфигурации отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md), [параметры проекта для конфигурации отладки Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), и [как: Настройка отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to Debug the DLL  
 Каждый из проектов в данном разделе создает библиотеку DLL. Нельзя запустить библиотеку DLL напрямую;она должна быть вызвана приложением, как правило, исполняемым файлом. Для получения дополнительной информации см. [Creating and Managing Visual C++ Projects](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Вызывающее приложение может удовлетворять любому из следующих критериев:  
  
-   Программа построена в другом проекте в том же решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], которое содержит библиотеку классов.  
  
-   Существующее приложение уже установлено на тестовом или рабочем компьютере.  
  
-   Программа расположена в Интернете и доступна по URL–адресу.  
  
-   Веб–приложение содержит веб–страницу, в которую внедрена библиотека DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Отладка вызывающего приложения  
 Для отладки библиотеки DLL, запустите отладку вызывающего приложения — как правило, это исполняемый файл или веб–приложение. Есть несколько способов её отладки.  
  
-   Если для вызывающего приложения имеется проект, можно открыть этот проект и запустить выполнение из меню **Отладка** . Для получения дополнительной информации см. [How to: Start Execution](http://msdn.microsoft.com/en-us/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
-   Если вызывающее приложение — это существующая программа, уже развернутая на рабочем или тестовом компьютере и уже выполняемая, можно присоединиться к нему. Используйте этот метод, если DLL — это элемент управления, размещенный в Internet Explorer или на веб–странице. Для получения дополнительной информации см. [How to: Attach to a Running Process](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
-   Можно выполнять отладку из проекта DLL. Дополнительные сведения см. в разделе [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Можно выполнять отладку из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Immediate** window. В этом случае окно **Интерпретация** выступает в качестве приложения.  
  
 Перед запуском отладки этого вызывающего приложения нужно задать точку останова в библиотеке классов. Для получения дополнительной информации см. [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). При срабатывании точки останова можно пошагово проходить по коду, наблюдая действия в каждой строке, до тех пор, пока не будет выделена возникшая проблема. Для получения дополнительной информации см. [Code Stepping Overview](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Controls on a Web Page  
 Чтобы отлаживать элемент управления веб–страницы, создайте страницу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , которая его содержит, если такая страница еще не существует. Затем следует расставить точки останова в коде веб–страницы и в коде элемента управления. Затем можно вызвать веб–страницу из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Перед запуском отладки этого вызывающего приложения нужно установить точку останова в DLL. При срабатывании точки останова можно пошагово проходить по коду, наблюдая действия в каждой строке, до тех пор, пока не будет выделена возникшая проблема. Для получения дополнительной информации см. [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> The Immediate Window  
 Можно вычислять функции или методы библиотеки DLL без вызывающего приложения. Происходит отладка во время разработки и используется окно **Интерпретация** . Для такой отладки выполните следующие действия, пока открыт проект DLL:  
  
1.  Откройте окно **Интерпретация** отладчика.  
  
2.  Чтобы проверить метод с именем `Test` в классе `Class1`, создайте экземпляр класса `Class1` путем ввода следующего кода C# в окне интерпретации. Этот управляемый код работает под Visual Basic и C++ с соответствующими изменениями синтаксиса:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     В C# все имена должны быть указаны полностью. Кроме того, любые методы или переменные должны находиться в текущем контексте сеанса отладки и в текущей области кода.  
  
3.  Предположим, что `Test` принимает один параметр `int` , вычислим `Test` с помощью окна **Интерпретация** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Результат будет напечатан в окне **Интерпретация** .  
  
4.  Можно продолжить отладку `Test` , установив в нем точку останова, а затем снова вычислив эту функцию:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Случится прерывание на точке останова и можно будет пройти `Test`в пошаговом режиме. После выполнения `Test`, отладчик вернется в режим разработки.  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)



