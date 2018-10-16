---
title: 'Практическое: отладка исполняемого файла, не в состав решения Visual Studio | Документация Майкрософт'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 241a1dbf3af5db726f344ab42d53de3fdd30db3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278793"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Практическое руководство. Отладка исполняемого файла, не входящего в состав решения Visual Studio.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда требуется отладка исполняемого файла, не являющегося частью проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Это может быть исполняемый файл, созданный вами без использования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или полученный от кого–нибудь еще.  
  
 Стандартным решением этой проблемы является запуск исполняемого файла (не из Visual Studio) и присоединение к нему с использованием отладчика [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе[подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Присоединение к приложению требует выполнения ряда операций вручную, что займет некоторое время. Возникающая задержка означает, что присоединение не поможет, если отлаживается проблема, возникающая в момент запуска программы. Кроме того, если отлаживается программа, которая не ожидает ввода пользователя и быстро завершается, может не хватить времени для присоединения к ней. Если установлен [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], для такой программы можно создать проект исполняемого файла.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Чтобы создать EXE–проект для существующего исполняемого файла  
  
1.  На **файл** меню, щелкните **откройте** и выберите **проекта**.  
  
2.  В **Открытие проекта** диалоговом окне в раскрывающемся списке рядом с полем **имя файла** выберите **все файлы проекта**.  
  
3.  Найдите исполняемый файл и щелкните **ОК**.  
  
     При этом создается временное решение, содержащее данный исполняемый файл.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Чтобы импортировать исполняемый файл в решение Visual Studio  
  
1.  На **файл** последовательно выберите пункты **добавить проект**, а затем нажмите кнопку **существующий проект**.  
  
2.  В **добавить существующий проект** диалоговом окне в раскрывающемся списке рядом с полем **имя файла** выберите **все файлы проекта**.  
  
3.  Найдите и выберите нужный исполняемый файл.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  Запустите исполняемый файл, выбрав команду выполнения, такие как **запустить**, из **Отладка** меню.  
  
    > [!NOTE]
    >  Не все языки программирования поддерживают исполняемые проекты. Если необходимо использовать эту возможность, установите [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
     При отладке исполняемого файла без исходного кода доступные возможности отладки ограничены, независимо от того, происходит ли присоединение к исполняемому файлу или же исполняемый файл добавляется в решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если исполняемый файл был скомпонован без отладочной информации в совместимом формате, доступные функции крайне ограничены. Если имеется исходный код,лучшим решением является его импорт в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и создание отладочной сборки исполняемого файла в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [DBG-файлы](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



