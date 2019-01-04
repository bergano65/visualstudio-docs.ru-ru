---
title: Перечислители | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26631c4b6ae6d6fb8d5bd00c772cc7f11943d459
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848104"
---
# <a name="enumerators"></a>Перечислители
В этом разделе перечислены типы данных перечислителя в API подключаемого модуля управления источник, подключаемый модуль системы управления версиями необходимо знать.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Код команды](../extensibility/command-code-enumerator.md)  
 Перечисляет параметры для [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md) функции.  
  
 [Сообщение](../extensibility/message-enumerator.md)  
 Перечисляет флаги, используемые для печати обратного вызова, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние файла в системе управления версиями.  
  
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние каталога в системе управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK подключаемого модуля управления источника и описывает включаемые ресурсы.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Запрашивает у пользователя Дополнительные параметры для данной команды.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функцию обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.  
  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.