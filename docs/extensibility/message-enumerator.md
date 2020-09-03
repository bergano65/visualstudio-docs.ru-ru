---
title: Перечислитель сообщений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702506"
---
# <a name="message-enumerator"></a>Перечислитель сообщений
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
 SCC_MSG_RTN_CANCEL возвратить из обратного вызова для указания отмены.

 Чтобы продолжить, SCC_MSG_RTN_OK вернуться из обратного вызова.

 SCC_MSG_INFO сообщение является информационным.

 SCC_MSG_WARNING сообщение является предупреждением.

 SCC_MSG_ERROR сообщение является ошибкой.

 SCC_MSG_STATUS сообщение предназначено для строки состояния.

 SCC_MSG_DOCANCEL нет текста; Интегрированная среда разработки возвращает `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL начинает цикл отмены.

 SCC_MSG_STOPCANCEL останавливает цикл отмены.

## <a name="see-also"></a>См. также раздел
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
