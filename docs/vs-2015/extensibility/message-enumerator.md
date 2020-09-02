---
title: Перечислитель сообщений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194344"
---
# <a name="message-enumerator"></a>Перечислитель сообщений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Следующие флаги используются для `TEXTOUTPROC` функции, которая является функцией обратного вызова, предоставляемой интегрированной средой разработки при вызове [сккопенпрожект](../extensibility/sccopenproject-function.md) (Дополнительные сведения о функции обратного вызова см. в разделе [лптекстаутпрок](../extensibility/lptextoutproc.md) ).  
  
 Если интегрированная среда разработки запрашивает отмену процесса, может появиться одно из сообщений об отмене. В этом случае подключаемый модуль системы управления версиями использует, `SCC_MSG_STARTCANCEL` чтобы задать отображение кнопки **Отмена** в интегрированной среде разработки. После этого можно отправить любой набор обычных сообщений. Если какой-либо из этих `SCC_MSG_RTN_CANCEL` операций возвращает, то подключаемый модуль завершает операцию и возвращает. Подключаемый модуль также периодически опрашивается, `SCC_MSG_DOCANCEL` чтобы определить, была ли отменена операция пользователем. По завершении всех операций или при отмене пользователем подключаемый модуль отправляется `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`Типы, SCC_MSG_WARNING и SCC_MSG_ERROR используются для сообщений, которые отображаются в прокручиваемом списке сообщений. `SCC_MSG_STATUS` — Это специальный тип, который указывает, что текст должен отображаться в строке состояния или в временной области отображения. Он не будет постоянно отображаться в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="members"></a>Участники  
 SCC_MSG_RTN_CANCEL  
 Возврат из обратного вызова для указания отмены.  
  
 SCC_MSG_RTN_OK  
 Чтобы продолжить, вернитесь из обратного вызова.  
  
 SCC_MSG_INFO  
 Сообщение является информационным.  
  
 SCC_MSG_WARNING  
 Сообщение является предупреждением.  
  
 SCC_MSG_ERROR  
 Сообщение является ошибкой.  
  
 SCC_MSG_STATUS  
 Сообщение предназначено для строки состояния.  
  
 SCC_MSG_DOCANCEL  
 Нет текста; Интегрированная среда разработки возвращает `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL` .  
  
 SCC_MSG_STARTCANCEL  
 Запускает цикл отмены.  
  
 SCC_MSG_STOPCANCEL  
 Останавливает цикл отмены.  
  
## <a name="see-also"></a>См. также:  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
