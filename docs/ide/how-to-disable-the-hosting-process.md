---
title: "Практическое руководство. Отключение ведущего процесса | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
Включение ведущего процесса может негативно повлиять на вызовы некоторых API. В таких случаях нужно отключить ведущий процесс, чтобы возвратить правильные результаты.  
  
### <a name="to-disable-the-hosting-process"></a>Отключение ведущего процесса  
  
1.  Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для проектов, не создающих исполняемые файлы (например, проектов библиотеки классов или службы), этот параметр отсутствует.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  Откройте вкладку **Отладка**.  
  
4.  Снимите флажок **Включить ведущий процесс Visual Studio**.  
  
 Когда ведущий процесс отключен, некоторые функции отладки недоступны или работают хуже. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).  
  
 Как правило, отключение ведущего процесса приводит к следующему:  
  
-   Увеличивается время, необходимое для начала отладки [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Недоступно вычисление выражений во время разработки.  
  
-   Недоступна отладка с частичным доверием.  
  
## <a name="see-also"></a>См. также

[Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)   
[Главный процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)