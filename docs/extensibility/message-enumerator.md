---
title: Иенмератор сообщения Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702506"
---
# <a name="message-enumerator"></a>Перечисление сообщений
Следующие флаги используются для `TEXTOUTPROC` функции, которая является функцией обратного вызова, которую предоставляет IDE, когда он вызывает [SccOpenProject](../extensibility/sccopenproject-function.md) (см. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) для получения подробной информации о функции обратного вызова).

 Если IDE попроситот отменить процесс, он может получить одно из сообщений об отмене. В этом случае плагин управления `SCC_MSG_STARTCANCEL` исходным элементом использует, чтобы попросить IDE отобразить кнопку **Отмена.** После этого может быть отправлен любой набор обычных сообщений. Если какой-либо из этих возвращается, `SCC_MSG_RTN_CANCEL`то плагин завершает операцию и возвращается. Плагин также периодически `SCC_MSG_DOCANCEL` проводит опросы, чтобы определить, отменил ли пользователь операцию. Когда все операции выполнены, или если пользователь отменил, `SCC_MSG_STOPCANCEL`плагин отправляет. Для `SCC_MSG_INFO`сообщений, отображаемых в списке прокрутки сообщений, используются типы SCC_MSG_WARNING и SCC_MSG_ERROR. `SCC_MSG_STATUS`— это особый тип, указывающий на то, что текст должен отображаться в панели состояния или временной зоне отображения. Он не остается постоянно в списке.

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
 SCC_MSG_RTN_CANCEL Возврат из обратного вызова, чтобы указать отмену.

 SCC_MSG_RTN_OK Возвращение из обратного вызова для продолжения.

 SCC_MSG_INFO Сообщение является информационным.

 SCC_MSG_WARNING сообщение является предупреждением.

 SCC_MSG_ERROR сообщение является ошибкой.

 SCC_MSG_STATUS сообщение предназначено для панели статуса.

 SCC_MSG_DOCANCEL Нет текста; IDE `SCC_MSG_RTN_OK` возвращается или `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL запускает цикл отмены.

 SCC_MSG_STOPCANCEL останавливает цикл отмены.

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
