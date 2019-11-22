---
title: 'How to: Invoke the Workflow Debugger | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292899"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Как вызвать отладчик рабочего процесса
Как правило, отладка рабочих процессов похожа на отладку программ, написанных на других языках программирования Visual Studio. Запуск отладчика рабочих процессов:

- Select **Attach to Process** on the **Debug** menu to select the running host process for your workflow instance. Эта процедура совпадает с процедурой прикрепления к хост-процессу в управляемом коде.

- Press **F5** to start running an instance of the workflow, or to continue to run after a breakpoint has been hit.

- Используйте удаленную отладку. For information on using remote debugging, see [How to: Enable Remote Debugging](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > If the workflow application targets the x86 architecture and is hosted on a machine running a 64 bit operating system, then remote debugging will not work unless [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] is installed on the remote machine or the target for the workflow application is changed to **Any CPU**.

### <a name="stepping-through-code"></a>Пошаговая отладка

- **Step In**: You can step into an activity using **F11**. Отладчик выполняет пошаговую отладку всех заданных обработчиков. Если обработчики не заданы, то действие пропускается, а в случае составного действия, которое содержит другие действия, выполняется вход в первое выполняющееся действие.

- **Step Out:** You can step out of an activity using **Shift-F11**. Выход из пошаговой отладки действия запускает текущее действие и все родственные действия на выполнение до завершения. Далее отладчик прерывается на текущем родительском объекте действия. При выходе из пошаговой отладки из кода обработчика, отладчик прерывается на действии, с которым связан обработчик.

- **Step Over**: You can step over an activity using **F10**. При обходе составного действия отладчик прерывается на первом исполняемом дочернем объекте составного действия. При обходе несоставного действия, например, действия <xref:System.Activities.Statements.Assign>, отладчик выполняет действие и связанные с ним обработчики и прерывается на следующем действии. Если выполняемое действие является последним дочерним действием в составном действии, то после выполнения отладчик прерывается на родительском действии.

### <a name="debugging-with-f5"></a>Отладка по клавише F5

- If you are building a Workflow Console Application project, simply press **F5** to begin debugging into your application and workflow. При создании отдельной библиотеки действий необходимо в качестве начального проекта подготовить исполняемое хост-приложение. To set a startup project in **Solution Explorer**, right-click the project name of the host and select **Set as StartUp Project**.

## <a name="see-also"></a>См. также раздел
 [How to: Set Breakpoints in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [Debugging Workflows with the Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)