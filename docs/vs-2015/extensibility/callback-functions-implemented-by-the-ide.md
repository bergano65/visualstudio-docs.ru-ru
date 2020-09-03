---
title: Функции обратного вызова, реализованные интегрированной средой разработки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: df2daef11303e85d5fe2d0bf33e3df038081db64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184535"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Функции обратного вызова, реализуемые интегрированной средой разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы упростить интеграцию с интегрированной средой разработки (IDE) и обеспечить единообразное взаимодействие с конечным пользователем, подключаемый модуль системы управления версиями может использовать функции обратного вызова, реализованные интегрированной средой разработки. Подключаемый модуль может вызывать эти функции в нужное время во время операции системы управления версиями для передачи информации в интегрированную среду разработки. Интегрированная среда разработки может затем отображать эти сведения как внедренные элементы в своем собственном ИНТЕРФЕЙСе. В этом сценарии у пользователя менее фрагментированный интерфейс, чем если бы подключаемый модуль использовал собственный пользовательский интерфейс.  
  
 Требуемый заголовочный файл — SCC. h. Расположение по умолчанию — \Program Филес\всип 8.0 \ Енвсдк\коммон\инк \\ . Он также находится в папке VSIP с примером подключаемого модуля системы управления версиями в \Program Филес\всип 8.0 \ MSSCCI \\ .  
  
## <a name="in-this-section"></a>в этом разделе  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функцию обратного вызова, используемую [сккопенпрожект](../extensibility/sccopenproject-function.md) для вывода сообщений из подключаемого модуля системы управления версиями через интегрированную среду разработки.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Описывает функцию обратного вызова, используемую [сккпопулателист](../extensibility/sccpopulatelist-function.md) , когда интегрированная среда разработки не имеет полного доступа к информации, доступной только для подключаемого модуля системы управления версиями, например полный список файлов в системе управления версиями.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Описывает функцию обратного вызова, используемую операцией [скккуеричанжес](../extensibility/sccquerychanges-function.md) .  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Описывает функцию обратного вызова, используемую операцией [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md) .  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Описывает функцию обратного вызова, заданную с помощью вызова [скксетоптион](../extensibility/sccsetoption-function.md) , который позволяет подключаемому модулю системы управления версиями обмениваться данными об изменениях имени обратно в интегрированную среду разработки.  
  
## <a name="related-sections"></a>См. также  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Открывает проект.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов на предмет их текущего состояния. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand` .  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Проверяет список каталогов и файлов в проекте или проектах, которые находятся в системе управления версиями. Каждый найденный каталог и имя файла передаются в функцию обратного вызова.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Проверяет изменения имен, внесенные в список файлов. Каждое имя файла передается в функцию обратного вызова вместе с состоянием изменения.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Задает широкий спектр параметров. Каждый параметр начинается с `SCC_OPT_xxx` и имеет собственный набор значений.  
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Описывает содержимое раздела Reference пакета SDK для подключаемого модуля системы управления версиями.
