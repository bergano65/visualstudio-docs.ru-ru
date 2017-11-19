---
title: "Как: отладка исполняемого файла, который не является частью решения Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be07be0e1374360a96b6672b095dcc039c6bb4f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Как: отладка исполняемого файла, который не является частью решения Visual Studio
Иногда требуется отладка исполняемого файла (файл .exe), не является частью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. Это может быть исполняемый файл, созданный вами без использования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или полученный от кого–нибудь еще.  
  
Стандартным решением этой проблемы является запуск исполняемого файла (не из Visual Studio) и присоединение к нему с использованием отладчика [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [присоединение к процессу под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Присоединение к приложению требует выполнения ряда операций вручную, что займет некоторое время. Возникающая задержка означает, что присоединение не поможет, если отлаживается проблема, возникающая в момент запуска программы. Кроме того, если отлаживается программа, которая не ожидает ввода пользователя и быстро завершается, может не хватить времени для присоединения к ней. Если у вас есть [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] установлен, можно создать проект исполняемого файла для такой программы.

> [!NOTE]
>  Не все языки программирования поддерживают исполняемые проекты.

При отладке исполняемого файла, который не является частью решения Visual Studio доступные функции отладки могут быть ограничены, является ли присоединение к исполняемому или исполняемый файл добавляется в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения.

- Если имеется исходный код,лучшим решением является его импорт в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и создание отладочной сборки исполняемого файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- При отсутствии исходного кода, и в том случае, если исполняемый файл был скомпонован без [отладочной информации,](../debugger/how-to-set-debug-and-release-configurations.md) в совместимом формате, доступные функции отладки ограничены. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Чтобы создать EXE–проект для существующего исполняемого файла  
  
1.  На **файл** меню, нажмите кнопку **откройте** и выберите **проекта**.  
  
2.  В **Открытие проекта** диалоговое окно, щелкните раскрывающийся список рядом с **имя файла** и выберите **все файлы проекта**.  
  
3.  Найдите исполняемый файл и нажмите кнопку **ОК**.  

    При этом создается временное решение, содержащее данный исполняемый файл.

5.  Запустите исполняемый файл, выбрав команду выполнения, таких как **запустить**, из **отладки** меню.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Чтобы импортировать исполняемый файл в решение Visual Studio  
  
1.  На **файл** последовательно выберите пункты **добавить проект**, а затем нажмите кнопку **существующий проект**.  
  
2.  В **добавить существующий проект** диалоговое окно, щелкните раскрывающийся список рядом с **имя файла** и выберите **все файлы проекта**.  
  
3.  Найдите и выберите нужный исполняемый файл.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  Запустите исполняемый файл, выбрав команду выполнения, таких как **запустить**, из **отладки** меню.    
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [DBG-файлы](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)