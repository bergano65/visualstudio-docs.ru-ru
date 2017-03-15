---
title: "Перечислители | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Источник подключаемые модули управления, перечислители"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Перечислители
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе перечислены типы данных перечислителя в API подключаемого модуля управления источник, подключаемый модуль системы управления версиями необходимо знать.  
  
## В этом подразделе  
 [Код команды](../extensibility/command-code-enumerator.md)  
 Перечисляет параметры [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md) функции.  
  
 [Сообщение](../extensibility/message-enumerator.md)  
 Перечисляет флаги, используемые для печати обратного вызова, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние файла в системе управления версиями.  
  
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние каталога в системе управления версиями.  
  
## Связанные подразделы  
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Пакет SDK подключаемого модуля управления источника определяет и описывает включенные ресурсы.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Пользователю предлагается для установки дополнительных параметров для данной команды.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающей стороны, если файл не соответствует критериям для `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функции обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль — интегрированной среды разработки.  
  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемого модуля управления источника.