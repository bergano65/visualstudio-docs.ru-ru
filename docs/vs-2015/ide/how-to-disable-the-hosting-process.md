---
title: Практическое руководство. Отключение ведущего процесса | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0266e14b3a03e6d8225e7ec9283fe727a9502e53
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54785885"
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Включение ведущего процесса может негативно повлиять на вызовы некоторых API. В таких случаях нужно отключить ведущий процесс, чтобы возвратить правильные результаты.  
  
### <a name="to-disable-the-hosting-process"></a>Отключение ведущего процесса  
  
1. Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Для проектов, не создающих исполняемые файлы (например, проектов библиотеки классов или службы), этот параметр отсутствует.  
  
2. В меню **Проект** выберите пункт **Свойства**.  
  
3. Откройте вкладку **Отладка**.  
  
4. Снимите флажок **Включить ведущий процесс Visual Studio**.  
  
   Когда ведущий процесс отключен, некоторые функции отладки недоступны или работают хуже. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).  
  
   Как правило, отключение ведущего процесса приводит к следующему:  
  
-   Увеличивается время, необходимое для начала отладки [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
-   Недоступно вычисление выражений во время разработки.  
  
-   Недоступна отладка с частичным доверием.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)   
 [Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Сборки во время разработки приложения](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
