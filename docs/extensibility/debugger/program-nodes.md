---
title: "Программа узлов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Программа узлов, контекст отладки"
  - "отладка [пакет SDK для отладки], программы узлов"
  - "узлы программы, добавление"
  - "сведения о заменяющих узлов программы"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Программа узлов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В терминах архитектуры отладчика, a **узел программы**.  
  
-   Упрощенное описание программы.  
  
-   Он может указать и процесс выполняется внутри и может быть вложенно, наконец, удаляется из и описания обработчика отладки \(DE\), который создал ее, если таковой имеется.  
  
-   Представляет  IDebugProgramNode2 обычно интерфейс, созданный DE или портом.  Узлы добавляются к порту с помощью программы [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Когда узел программы добавляется к порту, он добавляется к процессу, содержащую программу, которую представляет данный узел программы.  
  
 Когда\-то после запуска сеанса отладки, в зависимости от реализации пакета отладки, узлы программы используется для создания соответствующей программы.  Если процесс запрашивается для своих программ, перечисляются программы, по одному для каждого узла программы.  
  
 Перед тем как программа вложенна в интегрированной среде разработки необходимо только упрощенное описание программы.  Эти сведения можно получить из узла программы.  Как только программа вложенна в интегрированной среде разработки требуется отобразить более подробные сведения, такие как список всех потоков, работающих в программе.  Эти данные извлекаются из программы самой.  
  
## См. также  
 [Programs](../../extensibility/debugger/programs.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)