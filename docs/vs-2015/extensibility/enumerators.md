---
title: Перечислители | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991229"
---
# <a name="enumerators"></a>Перечислители.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе перечислены типы данных перечислителя в API подключаемого модуля управления источник, подключаемый модуль системы управления версиями необходимо знать.  
  
## <a name="in-this-section"></a>В этом разделе  
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
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.
