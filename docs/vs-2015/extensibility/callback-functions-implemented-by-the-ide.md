---
title: Функции обратного вызова, реализованные интегрированной среды разработки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84533d95eb6bc0f6433d0b021d429c13e504c13d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212788"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Функции обратного вызова, реализуемые интегрированной средой разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы интеграция с по интегрированной среде разработки (IDE) как простой, как можно и для обеспечения единой конечных пользователей, подключаемый модуль системы управления версиями можно использовать функции обратного вызова, реализуемые интегрированной среды разработки с. Подключаемый модуль может вызывать эти функции в соответствующее время во время операции управления версиями для передачи информации в интегрированную среду разработки; Эти сведения затем можно отобразить интегрированной среды разработки как внедренные элементы в его собственном пользовательском Интерфейсе. Пользователь имеет возможность менее фрагментированных в этом сценарии, чем если подключаемый модуль используются свой UI.  
  
 Обязательный заголовок он scc.h. Расположение по умолчанию — \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Он также находится в папке VSIP, имеющий образец подключаемого модуля управления источника во \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>В этом разделе  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функцию обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Описывает функцию обратного вызова, используемый [SccPopulateList](../extensibility/sccpopulatelist-function.md) при интегрированной среды разработки не имеет полный доступ к информации, которая доступна только для системы управления версиями, подключаемый модуль, например полный список файлов в системе управления версиями.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Описывает функцию обратного вызова, используемый [SccQueryChanges](../extensibility/sccquerychanges-function.md) операции.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Описывает функцию обратного вызова, используемый [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) операции.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Описывает функцию обратного вызова, установленный вызовом метода для [SccSetOption](../extensibility/sccsetoption-function.md) , позволяющий системы управления версиями, подключаемый модуль для связи имя изменения обратно в интегрированную среду разработки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Открывает проект.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найден передается функции обратного вызова.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Проверяет имя изменения, внесенные в список файлов. Имя каждого файла передается функции обратного вызова, вместе с его состоянием изменения.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Задает разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет свой собственный определенный набор значений.  
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Описывает содержимое в справочном разделе пакета SDK подключаемого модуля управления источника.

