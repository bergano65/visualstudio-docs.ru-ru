---
title: "Перечислитель сообщений | Microsoft Docs"
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
  - "Перечислитель сообщений"
  - "исходный элемент управления подключаемые модули, перечисления сообщений"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Перечислитель сообщений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Следующие флаги используются для `TEXTOUTPROC` функции, которая является функцией обратного вызова, интегрированная среда разработки предоставляет при вызове [SccOpenProject](../extensibility/sccopenproject-function.md) \(см. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) сведения о функции обратного вызова\).  
  
 Если IDE будет предложено отменить процесс, появляется одно из сообщений "Отмена". В этом случае используется подключаемый модуль управления версиями `SCC_MSG_STARTCANCEL` попросить IDE для отображения **Отменить** кнопки. После этого любой набор обычные сообщения могут быть отправлены. Если любой из этих возвращает `SCC_MSG_RTN_CANCEL`, подключаемый модуль завершает работу операция, и возвращает. Подключаемый модуль также опрашивает `SCC_MSG_DOCANCEL` периодически, чтобы определить, если операция отменена пользователем. Если все операции выполняются, или если пользователь отменил, подключаемый модуль отправляет `SCC_MSG_STOPCANCEL`.`SCC_MSG_INFO`, SCC\_MSG\_WARNING, и SCC\_MSG\_ERROR типы используются для сообщений, которые отображаются в прокруткой списка сообщений.`SCC_MSG_STATUS` — особый тип, указывает, что текст, будут отображаться в строке состояния или временные отображаемой области. Не будет окончательно в списке.  
  
## Синтаксис  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## Участники  
 SCC\_MSG\_RTN\_CANCEL  
 Отмена возврата из обратного вызова для указания.  
  
 SCC\_MSG\_RTN\_OK  
 Возврата из обратного вызова, чтобы продолжить.  
  
 SCC\_MSG\_INFO  
 Сообщение является информационным.  
  
 SCC\_MSG\_WARNING  
 Сообщение является предупреждением.  
  
 SCC\_MSG\_ERROR  
 Сообщение является ошибкой.  
  
 SCC\_MSG\_STATUS  
 Сообщение предназначено для строки состояния.  
  
 SCC\_MSG\_DOCANCEL  
 Нет текста; Возвращает IDE `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL`.  
  
 SCC\_MSG\_STARTCANCEL  
 Запускает цикл "Отмена".  
  
 SCC\_MSG\_STOPCANCEL  
 Останавливает цикла "Отмена".  
  
## См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)