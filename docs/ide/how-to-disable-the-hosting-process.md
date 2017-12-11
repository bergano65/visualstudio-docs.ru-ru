---
title: "Практическое руководство. Отключение ведущего процесса | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94d40fe18ff4cca228fb39ab16bcfaa6ac42a172
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 [Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Сборки во время разработки приложения](http://msdn.microsoft.com/en-us/c9497d62-3b7b-4449-88e8-cf27acc9efe6)