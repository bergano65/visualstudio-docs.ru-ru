---
title: "Функции обратного вызова, реализуемый интегрированной среды разработки | Microsoft Docs"
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
  - "исходный элемент управления подключаемые модули, функции обратного вызова"
  - "функции обратного вызова, подключаемые модули управления версиями"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Функции обратного вызова, реализуемый интегрированной среды разработки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Чтобы интеграция с интегрированную среду разработки \(IDE\) как простой, как можно и для обеспечения единой конечного пользователя, подключаемый модуль системы управления версиями обратного вызова функции используются, реализованные в Интегрированной среде разработки. Подключаемый модуль может вызывать эти функции в соответствующее время во время операции управления версиями для передачи информации в Интегрированной среде разработки; затем Интегрированной среде разработки можно отобразить эти сведения как внедренные элементы в свой собственный Интерфейс. Пользователь имеет менее фрагментированным опыт в этом сценарии, чем если подключаемый модуль, применяемых свой UI.  
  
 Обязательный заголовок файла — scc.h. Расположение по умолчанию — \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\. Он также находится в папке VSIP, с исходного образца подключаемого модуля управления в \\Program Files\\VSIP 8.0\\MSSCCI\\.  
  
## В этом подразделе  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функции обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль — интегрированной среды разработки.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Описывает функции обратного вызова, используемой [SccPopulateList](../extensibility/sccpopulatelist-function.md) при интегрированной среды разработки не имеет полный доступ к информации, доступной только для системы управления версиями, подключаемый модуль, например полный список файлов в системе управления версиями.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Описывает функции обратного вызова, используемый [SccQueryChanges](../extensibility/sccquerychanges-function.md) операции.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Описывает функции обратного вызова, используемый [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) операции.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Описывает набор путем вызова функции обратного вызова [SccSetOption](../extensibility/sccsetoption-function.md) позволяющий системы управления версиями, подключаемый модуль взаимодействия имя изменений обратно в Интегрированной среде разработки.  
  
## Связанные подразделы  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Открывает проект.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающей стороны, если файл не соответствует критериям для `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Проверяет список каталогов и файлов в проект или проекты, которые находятся в системе управления версиями. Каждый каталог и имя файла найти передается функции обратного вызова.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Проверяет имя изменения, внесенные в список файлов. Имя каждого файла передается функции обратного вызова, вместе с его состоянием изменения.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Устанавливает самые разнообразные параметры. Каждый параметр начинается с `SCC_OPT_xxx` и имеет свой собственный набор определенных значений.  
  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)  
 Описывает содержимое в справочном разделе пакета SDK подключаемого модуля управления источника.