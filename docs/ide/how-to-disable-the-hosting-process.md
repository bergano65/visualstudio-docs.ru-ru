---
title: "Практическое руководство. Отключение главного процесса | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ведущий процесс, отключение"
  - "vshost.exe, отключение ведущего процесса"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Отключение главного процесса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Вызовы к некоторым API могут быть затронуты, когда процесс размещения включен.  В таких случаях для возвращения правильных результатов нужно отключать главный процесс.  
  
### Чтобы отключить главный процесс  
  
1.  Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Проекты, которые не создают исполняемые файлы \(например, проекты библиотеки классов или службы\) не имеют этот параметр.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  Перейдите на вкладку **Отладка**.  
  
4.  Снимите флажок **Разрешить главный процесс Visual Studio**.  
  
 Когда главный процесс отключен, некоторые функции отладки недоступны, а также может снизиться производительность.  Для получения дополнительной информации см. [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md).  
  
 Обычно при отключении главного процесса происходит следующее:  
  
-   Увеличивается время отладки приложений [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Вычисление выражений в процессе разработки недоступно.  
  
-   Отладка с частичным доверием недоступна.  
  
## См. также  
 [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)   
 [Главный процесс \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/ru-ru/c9497d62-3b7b-4449-88e8-cf27acc9efe6)