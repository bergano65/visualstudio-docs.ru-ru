---
title: Практическое руководство. Отключение ведущего процесса | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47264ef7f1a6a2bd1a4ad3da59f53836f9ebb902
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-the-hosting-process"></a>Практическое руководство. Отключение ведущего процесса
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

[Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md)   
[Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)