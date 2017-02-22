---
title: "Основные понятия отладчика | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки]"
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Основные понятия отладчика
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Для построения для отладки Visual Studio пакета, необходимо ознакомиться с архитектуры принципы, используемые при разработке пакета.  
  
## Содержание  
 [Сеанс отладки](../../extensibility/debugger/debug-session.md)  
 Объясняет роль сеанса в архитектуре отладки.  
  
 [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Указывает, что сервер в терминах архитектуры отладки в обоих абстрактных и физических термина ".  
  
 [Поставщикам портов](../../extensibility/debugger/port-suppliers.md)  
 Указывает, что поставщик порта в терминах архитектуры отладки.  
  
 [Порты](../../extensibility/debugger/ports.md)  
 Указывает, что порт в терминах архитектуры отладки.  
  
 [Процессы](../../extensibility/debugger/processes.md)  
 Указывает, что процесс в терминах архитектуры отладки.  
  
 [Программа узлов](../../extensibility/debugger/program-nodes.md)  
 Определяет узел программы в терминах архитектуры отладки, включая как он может указать и он выполняется внутри процесса.  
  
 [Programs](../../extensibility/debugger/programs.md)  
 Определяет программу в терминах архитектуры отладки.  
  
 [Потоки](../../extensibility/debugger/threads.md)  
 Определяет характеристики потоков в терминах архитектуры отладки.  
  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)  
 Указывает кадр стека в терминах архитектуры отладки.  Кадр стека абстракция стека, предоставляющий контекст выполнения потока.  
  
 [Модули](../../extensibility/debugger/modules.md)  
 Определяет модуль в терминах архитектуры отладки, такие как физический контейнер кода, например исполняемый файл или библиотеку DLL.  
  
 [Точки останова](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Указывает тип точки 3 останова\-ожидающего решения, границ и ошибка\-в терминах архитектуры отладки.  
  
## Связанные разделы  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как отладчик \(DE\) работает синхронно в коде, документации и контекстов оценки выражений.  Описание для каждой из 3 контекстов, расположение соответствующей позиции или evaluation.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Содержит общие сведения о компонентах отладки Visual Studio, которые включают обработчик отладки \(DE\), средство оценки выражений \(EE\), и обработчик символов \(SH\).  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.