---
title: "Включение параметров отладки в Visual C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG - параметр компилятора [C++]"
  - "_DEBUG - макрос"
  - "утверждения, включение средств отладки"
  - "D_DEBUG - параметр компилятора"
  - "отладочные построения, MFC - библиотека"
  - "отладка [C++], включение средств отладки"
  - "отладка [MFC], включение средств отладки"
  - "MFC - библиотеки, отладочная версия"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Включение параметров отладки в Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] такие функции отладки, как утверждения, доступны при компиляции программы с заданным символом **\_DEBUG**.  **\_DEBUG** можно задать одним из двух способов.  
  
-   Указать **\# define \_DEBUG** в исходном коде.  
  
-   Указать параметр компилятора **\/D\_DEBUG**. \(При создании проекта в Visual Studio с использованием мастеров **\/D\_DEBUG**  задается автоматически в конфигурации отладчика.\)  
  
 Когда задан параметр **\_DEBUG**, компилятор компилирует разделы кода, заключенные между операторами **\#ifdef \_DEBUG** и `#endif`.  
  
 Конфигурация отладчика программы MFC должна компоноваться с версией отладчика библиотеки MFC.  Файлы заголовков MFC определяют точную версию используемой для компоновки библиотеки MFC на основе заданных символов, таких как **\_DEBUG** и **\_UNICODE**.  Дополнительные сведения см. в разделе [Версии библиотеки MFC](/visual-cpp/mfc/mfc-library-versions).  
  
## См. также  
 [Отладка машинного кода](../debugger/debugging-native-code.md)   
 [Параметры проекта для конфигурации отладки C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)