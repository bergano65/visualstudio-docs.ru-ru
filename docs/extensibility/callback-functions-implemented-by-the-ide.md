---
title: Функции обратного вызова, реализуемый интегрированной среды разработки | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="callback-functions-implemented-by-the-ide"></a>Функции обратного вызова, реализуемый интегрированной среды разработки
Чтобы интеграция с интегрированной среды разработки (IDE) как прозрачную максимально и для обеспечения единой конечного пользователя, подключаемый модуль системы управления версиями обратного вызова функции используются, реализованным в Интегрированной среде разработки. Подключаемый модуль может вызывать эти функции в соответствующее время во время операции управления версиями для передачи информации в Интегрированной среде разработки; затем интегрированной среды разработки можно отобразить эту информацию как внедренные элементы в свой собственный Интерфейс. Пользователь имеет менее фрагментированных опыт в этом сценарии, чем если подключаемый модуль, применяемых собственного пользовательского интерфейса.  
  
 Обязательный заголовок файла — scc.h. Расположение по умолчанию — \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Она также содержится в папке VSIP с образец подключаемого модуля управления источника в \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>В этом разделе  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функции обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Описывает функции обратного вызова, используемый [SccPopulateList](../extensibility/sccpopulatelist-function.md) при интегрированной среды разработки не имеет полный доступ к информации, доступной только для системы управления версиями, такие как полный список файлов в системе управления версиями.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Описывает функции обратного вызова, используемый [SccQueryChanges](../extensibility/sccquerychanges-function.md) операции.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Описывает функции обратного вызова, используемый [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) операции.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Описывает функцию обратного вызова, задать с помощью вызова [SccSetOption](../extensibility/sccsetoption-function.md) , позволяющий системы управления версиями для связи, имя изменения обратно в интегрированную среду разработки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Открывает проект.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущего состояния. Кроме того, использует `pfnPopulate` функции для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найден передается функции обратного вызова.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Проверяет имя изменения, внесенные в список файлов. Имя каждого файла передается функции обратного вызова, вместе с его состоянием изменений.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Устанавливает самые разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет собственный набор определенных значений.  
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Описывает содержимое в справочном разделе пакета SDK подключаемого модуля управления источника.