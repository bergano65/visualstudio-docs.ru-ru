---
title: Отладка приложения, который не является частью решения Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
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
ms.openlocfilehash: 6930360254111533ac635a404d203a87bbdd767e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874314"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Отладка приложения, который не является частью решения Visual Studio (C++, C#, Visual Basic, F#)

Вы можете выполнить отладку приложения (*.exe* файл), не входит в состав решения Visual Studio. Вы или кто-то другой может созданные приложения вне Visual Studio, или приложения, полученный из где-то еще. 

Обычно для отладки приложения, которое не существует в Visual Studio — запустить приложение вне Visual Studio, а затем подключите к ней с помощью **присоединение к процессу** в отладчике Visual Studio. Дополнительные сведения см. в разделе [присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Подключение к приложению требует ручного действия, которые принимают несколько секунд. Из-за этой задержки присоединение не поможет, отладка проблемы запуска, или приложение, которое не ожидает от пользователя ввода и быстро завершается. 

В таких ситуациях можно создать проект Visual Studio EXE для приложения или импортировать его в существующую коллекцию C#, Visual Basic или C++ решения. Не все языки программирования поддерживают исполняемые проекты. 

>[!IMPORTANT]
>Возможности отладки для приложения, которое не был собран в Visual Studio ограничены ли вы подключите к приложению, или добавьте в решение Visual Studio. 
>
>Если у вас есть исходный код, лучше всего импортировать код в проект Visual Studio. Затем запустите отладочную сборку приложения.
>
>Если у вас нет исходного кода, и приложение не имеет [отладочная информация](../debugger/how-to-set-debug-and-release-configurations.md) в формате, совместимом, доступные возможности отладки очень мало. 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Чтобы создать новый проект EXE для существующего приложения  
   
1. В Visual Studio выберите **файл** > **откройте** > **проекта**.  
   
1. В **Открытие проекта** выберите **все файлы проекта**, если еще не выбран, в раскрывающемся списке рядом с полем **имя файла**.  
   
1. Перейдите к *.exe* файл, выберите его и выберите **откройте**.  
   
   Файл появится в новой, временные решения Visual Studio.

1. Начните отладку приложения, выбрав команду выполнения, например **начать отладку**, из **Отладка** меню.    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Чтобы импортировать приложение в существующее решение Visual Studio  
  
1.  С помощью C++ C#, или выберите решение Visual Basic в Visual Studio **файл** > **добавить** > **существующий проект**.  
  
1. В **Открытие проекта** выберите **все файлы проекта**, если еще не выбран, в раскрывающемся списке рядом с полем **имя файла**.  
   
1. Перейдите к *.exe* файл, выберите его и выберите **откройте**.  
   
   Файл отображается как новый проект в текущее решение.  
   
1. С новым файлом выбран, начните отладку приложения, выбрав команду выполнения, например **начать отладку**, из **Отладка** меню.    
  
### <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [DBG-файлы](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))