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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204568"
---
# <a name="enumerators"></a>Enumerators
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе перечислены типы данных перечислителя в интерфейсе API подключаемого модуля системы управления версиями, о которых должен быть знаком подключаемый модуль системы управления версиями.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Код команды](../extensibility/command-code-enumerator.md)  
 Перечисляет параметры для функций [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [сккпопулателист](../extensibility/sccpopulatelist-function.md) .  
  
 [Message](../extensibility/message-enumerator.md)  
 Перечисляет флаги, используемые для обратного вызова печати, [лптекстаутпрок](../extensibility/lptextoutproc.md).  
  
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)  
 Содержит именованные постоянные значения, которые определяют состояние файла в системе управления версиями.  
  
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)  
 Содержит именованные постоянные значения, которые определяют состояние каталога в системе управления версиями.  
  
## <a name="related-sections"></a>См. также  
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK для подключаемого модуля системы управления версиями и описывает входящие ресурсы.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Запрашивает у пользователя дополнительные параметры для данной команды.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов на предмет их текущего состояния. Кроме того, использует `pfnPopulate` функцию для уведомления вызывающего объекта, если файл не соответствует критериям для `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функцию обратного вызова, используемую [сккопенпрожект](../extensibility/sccopenproject-function.md) для вывода сообщений из подключаемого модуля системы управления версиями через интегрированную среду разработки.  
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Содержит полный список всех элементов в интерфейсе API подключаемого модуля системы управления версиями.
