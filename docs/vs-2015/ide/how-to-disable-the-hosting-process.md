---
title: Практическое руководство. Отключение ведущего процесса | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a3c2eee43d333ee7b58907a8471f4be9815bd47
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558668"
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Disable the Hosting Process](https://docs.microsoft.com/visualstudio/ide/how-to-disable-the-hosting-process).  
  
Включение ведущего процесса может негативно повлиять на вызовы некоторых API. В таких случаях нужно отключить ведущий процесс, чтобы возвратить правильные результаты.  
  
### <a name="to-disable-the-hosting-process"></a>Отключение ведущего процесса  
  
1.  Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Для проектов, не создающих исполняемые файлы (например, проектов библиотеки классов или службы), этот параметр отсутствует.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  Откройте вкладку **Отладка**.  
  
4.  Снимите флажок **Включить ведущий процесс Visual Studio**.  
  
 Когда ведущий процесс отключен, некоторые функции отладки недоступны или работают хуже. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).  
  
 Как правило, отключение ведущего процесса приводит к следующему:  
  
-   Увеличивается время, необходимое для начала отладки [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
-   Недоступно вычисление выражений во время разработки.  
  
-   Недоступна отладка с частичным доверием.  
  
## <a name="see-also"></a>См. также  
 [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)   
 [Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Сборки во время разработки приложения](http://msdn.microsoft.com/en-us/c9497d62-3b7b-4449-88e8-cf27acc9efe6)



