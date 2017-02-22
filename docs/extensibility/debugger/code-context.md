---
title: "Контекст кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [отладка SDK] контексты"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Контекст кода
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IN [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, a контекст кода.  
  
-   Предоставляет абстракцию позиции в коде, как она известна обработчик отладки \(DE\).  Для большинства архитектур времени выполнения, сегодня контекст кода можно рассматривать как адреса в потоке инструктирования о программе.  Для нетрадиционных языков, в которых код не может быть представлен инструкциям, контекст кода может быть представлены некоторые.  
  
-   Описывает текущую позицию в потоке выполнения, отлаживанными программы.  
  
-   Существует только когда программа остановлена в точке останова.  
  
-   Имеет соответствующий контекст рисования.  
  
-   Реализует IDebugCodeContext2 интерфейс.  
  
## См. также  
 [Контекст документа](../../extensibility/debugger/document-context.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)