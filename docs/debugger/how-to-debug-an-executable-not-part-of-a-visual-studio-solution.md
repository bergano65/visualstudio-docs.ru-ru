---
title: 'Практическое: отладка исполняемого файла, который не является частью решения Visual Studio | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84c4acdc2cf4324c76dbbf7fe0b39ca9715b3c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279106"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Практическое: отладка исполняемого файла, который не является частью решения Visual Studio
В некоторых случаях требуется отладить исполняемый (файл.exe), который не является частью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. Это может быть исполняемый файл, созданный вами без использования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или полученный от кого–нибудь еще.  
  
Стандартным решением этой проблемы является запуск исполняемого файла (не из Visual Studio) и присоединение к нему с использованием отладчика [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Присоединение к приложению требует выполнения ряда операций вручную, что займет некоторое время. Возникающая задержка означает, что присоединение не поможет, если отлаживается проблема, возникающая в момент запуска программы. Кроме того, если отлаживается программа, которая не ожидает ввода пользователя и быстро завершается, может не хватить времени для присоединения к ней. Если у вас есть [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] установлен, можно создать проект исполняемого файла для такой программы.

> [!NOTE]
>  Не все языки программирования поддерживают исполняемые проекты.

При отладке исполняемого файла, который не является частью решения Visual Studio, доступные возможности отладки могут быть ограничены, при присоединении к выполняющемуся исполняемого файла или добавлении исполняемый файл для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения.

- Если имеется исходный код,лучшим решением является его импорт в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и создание отладочной сборки исполняемого файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Если у вас нет исходного кода, и в том случае, если исполняемый файл был скомпонован без [отладочная информация](../debugger/how-to-set-debug-and-release-configurations.md) в формате, совместимом, доступные возможности отладки, очень мало. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Чтобы создать EXE–проект для существующего исполняемого файла  
  
1.  На **файл** меню, щелкните **откройте** и выберите **проекта**.  
  
2.  В **Открытие проекта** диалоговом окне в раскрывающемся списке рядом с полем **имя файла** выберите **все файлы проекта**.  
  
3.  Найдите исполняемый файл и щелкните **ОК**.  

    При этом создается временное решение, содержащее данный исполняемый файл.

5.  Запустите исполняемый файл, выбрав команду выполнения, такие как **запустить**, из **Отладка** меню.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Чтобы импортировать исполняемый файл в решение Visual Studio  
  
1.  На **файл** последовательно выберите пункты **добавить проект**, а затем нажмите кнопку **существующий проект**.  
  
2.  В **добавить существующий проект** диалоговом окне в раскрывающемся списке рядом с полем **имя файла** выберите **все файлы проекта**.  
  
3.  Найдите и выберите нужный исполняемый файл.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  Запустите исполняемый файл, выбрав команду выполнения, такие как **запустить**, из **Отладка** меню.    
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [DBG-файлы](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))